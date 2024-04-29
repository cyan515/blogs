# Scala-CLI でシングルバイナリを吐かせてみるテスト

## ことの発端
ある日 Twitter で時間を溶かしているとこんな記事を見つけた。

[Scala Nativeがいつのまにかシングルバイナリを吐けるようになっていた](https://blog.3qe.us/entry/2023/06/14/203958)

いい感じに配布しやすい形で何か作れないかなぁとちょうど思っており、Scala 自体にも前々から興味はあったため、これに飛びついた、という次第。

## 環境構築
毎度毎度苦しむことでおなじみの環境構築。御多分にもれず今回も祝日の半日を飛ばすというポンコツっぷり。使用 OS は Windows です。

結論から書きます。最終的にシングルバイナリを吐けるようになるまでにやったことは以下です。やった順番通りに書きます。

- [Scala-CLI のインストール](https://scala-cli.virtuslab.org/)
- [LLVM のインストール](https://github.com/llvm/llvm-project/releases/tag/llvmorg-18.1.4)
- [sbt のインストール](https://www.scala-sbt.org/release/docs/Setup.html)
- [Visual Studio のインストール](https://visualstudio.microsoft.com/ja/vs/community/)

それぞれ何のツールなのかは~~よくわかってない~~世の中にもっといい記事があると思いますので、譲ります。

それぞれ入れ方を順に説明します。

### Scala-CLI のインストール
これはそんなに問題ないと思います。リンクを開いてすこし下ればわかりやすくボタンが置いてあるので、落とします。インストーラの指示に従います。
![image](https://gist.github.com/assets/81094959/9167ef1c-2cc9-4dc3-97a1-f910c4acfe47)

今回使いたい package 機能は、使う際 `--power` オプションをつけなきゃいけないのですが、毎回付けるの面倒なので付けなくていいようにデフォルト設定を変えます。[こちらの記事](https://blog.3qe.us/entry/2023/12/20/011354#Scala%E3%82%A2%E3%83%97%E3%83%AA%E3%82%B1%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3%E3%82%92%E3%83%91%E3%83%83%E3%82%B1%E3%83%BC%E3%82%B8%E3%81%97%E3%81%A6%E3%81%BF%E3%82%88%E3%81%86) を参考にしてます。
```cmt
% scala-cli config power true
```

この時点で、おそらく以下のコマンドでバイナリ自体は吐けるようになってると思います。
```cmd
% scala-cli package test.sc
```
`test.sc` の中身はこんな感じ。一瞬で終了しちゃわないように、入力待ちを入れます。
```scala:test.sc
println("Hello, Scala!")
scala.io.StdIn.readLine()
```
で、単独実行可能なシングルバイナリを吐くコマンドは
```cmd
% scala-cli package test.sc --native
```
なのですが、この時点だとおそらくエラーがだらだら出てきます。私の場合、`#include <stdio.h>` が見つからない、みたいなやつが大量に出てきました。

スタックトレースがログファイルに吐かれており、こんな感じでした。
```scala
scala.build.errors.ScalaNativeBuildError: Error compiling with Scala Native
  scala.cli.commands.package0.Package$.buildNative$$anonfun$1(Package.scala:1091)
  scala.build.EitherCps$Helper.apply(EitherCps.scala:19)
  scala.cli.commands.package0.Package$.buildNative(Package.scala:1095)
  scala.cli.commands.package0.Package$.doPackage$$anonfun$1(Package.scala:400)
  scala.build.EitherCps$Helper.apply(EitherCps.scala:19)
  scala.cli.commands.package0.Package$.doPackage(Package.scala:526)
  scala.cli.commands.package0.Package$.runCommand(Package.scala:155)
  scala.cli.commands.package0.Package$.runCommand(Package.scala:71)
  scala.cli.commands.ScalaCommand.run(ScalaCommand.scala:376)
  scala.cli.commands.ScalaCommand.run(ScalaCommand.scala:358)
  caseapp.core.app.CaseApp.main(CaseApp.scala:157)
  scala.cli.commands.ScalaCommand.main(ScalaCommand.scala:343)
  caseapp.core.app.CommandsEntryPoint.main(CommandsEntryPoint.scala:166)
  scala.cli.ScalaCliCommands.main(ScalaCliCommands.scala:125)
  scala.cli.ScalaCli$.main0(ScalaCli.scala:286)
  scala.cli.ScalaCli$.main(ScalaCli.scala:114)
  scala.cli.ScalaCli.main(ScalaCli.scala)
```

そこで、調べなおして[この記事](https://blog.3qe.us/entry/2023/01/07/211417#%E3%83%8D%E3%82%A4%E3%83%86%E3%82%A3%E3%83%96%E3%83%91%E3%83%83%E3%82%B1%E3%83%BC%E3%82%B8%E3%83%B3%E3%82%B0)や[この記事](https://zenn.dev/110416/articles/e3234fdc2d1aa7#%E3%82%BB%E3%83%83%E3%83%88%E3%82%A2%E3%83%83%E3%83%97)に当たりました。

なるほど、どうやら LLVM/sbt/clang/clang++ といったものが必要だと。というわけで入れていきます。

### LLVM のインストール
ダウンロードページは[こちら](https://releases.llvm.org/download.html)。

何種類かダウンロードする方法があるみたいですが、
私は [GitHub](https://github.com/llvm/llvm-project/releases/tag/llvmorg-18.1.4) からにしました。
バージョンはこれ以降なら動くんじゃないかなと思います（たぶん）。

インストーラが途中、パス通すかどうかみたいなのを聞いてきます。ラジオボタンで選択式なのですが、デフォが通さないになってますので、楽したい人は注意です。

### sbt のインストール
ダウンロードページは[こちら](https://www.scala-sbt.org/release/docs/Installing-sbt-on-Windows.html)。

こちらも何種類かダウンロード方法があるようですが、
> Install sbt with cs setup

こちらから実施しました。インストーラの指示に従って実行し、完了後に
```cmd
scala -version
```
でちゃんとバージョンが表示されるか確かめて、終わりです。

### Visual Studio のインストール
~~これに至ってはなんで必要なのかあんま理解してなかったり~~  
[こちらの記事](https://qiita.com/semiflat/items/43988856501ca94526e4) を参考に進めます。というか
> Build Tools for Visual Studio 2022 インストール手順

をまんま実施するだけです。たすかる～。

## おめあてのシングルバイナリを吐けることを確かめる
ここまで進めれば環境構築としては終わりのはずです。
```cmd
% scala-cli package test.sc --native
```
を実行すると `test.exe` ができると思いますので、これを実行して、期待通りの動作（文字が表示されて Enter 押したら消える）をするのを確認して完了になります。お疲れさまでした。

## ここには書かなかったけど必要であろうこと
- JDK のインストール
  - ゼロから構築する際には必要だと思います。私は元々入れててパスも通してました。
  - ちなみに、私の環境の JDK のバージョンは 21 で、sbt の推奨バージョンではないですが、今のところ特に問題なく動いてます。

## おわりに
普段から IDE におんぶにだっこなので、こういうの極端に弱くてダメですね。
反省はしてるし今後はやってかないといけないなぁと思ってはおりますが二度とやりたくないです。正直。

## 参考サイト

既に紹介したものも含めて、今回参考にした記事を挙げます。

- [Scala Nativeがいつのまにかシングルバイナリを吐けるようになっていた](https://blog.3qe.us/entry/2023/06/14/203958)
- [初心者向け: Scala CLIでScalaをはじめよう](https://blog.3qe.us/entry/2023/12/20/011354)
- [Scala-CLIを使うとScalaをいきなりバイナリに変換できてすごいので紹介したい](https://blog.3qe.us/entry/2023/01/07/211417)
- [【Scala初心者向け】sbtを触ってみよう！](https://www.casleydi.com/blog/engineer/104/)
- [Clangのインストール](https://students-tech.blog/post/install-clang.html)
- [Build Tools for Visual Studio 2022 導入](https://qiita.com/semiflat/items/43988856501ca94526e4)
