# Hello、ラムダ式！

## FP の利点
- immutability と型推論によるバグ除去
- 並列可能性
- 高い表現力
- 簡潔、高い SN 比
- 直観的

## Stream v.s. Iterator
後者は万能だが、「多芸は無芸」。前者は、合計値を得る、条件によって抽出する、別の型の object に変換する、等、目的に特化した API を備えており、可読性に寄与する。

## 高階関数によるポリシーの強制
関数を第一級市民として扱うことが可能になったことで、処理を他の箇所に注入するということが気軽にできるようになり、関心の分離に置いて有利。  
所謂 Strategy pattern と一緒だが、記述すべきコード量が段違い。

# コレクションの使用
はい。

# 文字列、コンパレータ、フィルタ

## 文字列
`String#chars` で `char` の `Stream` を得られる。

## コンパレータ
純粋なコンパレータだけじゃなくて、差を計算する method とかを流用することもできる。
例えば、`Person` というクラスに `ageDifference(Person):int` みたいな method があれば、年齢による sort はこれを利用しさえすればよい。
`Comparator.compareing(Person::getAge)` とかでもよい。

## コレクタ
`Collectors` の中の `toList` `toSet` `toMap` `joining` `mapping` `collectingAndThen` `minBy` `maxBy` など。

## フィルタ
`File#listFiles` でディレクトリにある全ファイルを含む `Stream` を生成できる。ファイル名だけ欲しいなら `File#list`。  
`Files#list(Path)` は、指定したパスに存在するファイルを列挙する。  
`flatMap`: モナド合成

# ラムダ式で設計する
- Strategy pattern を高階関数で設計
- delegation をする際、何らかの object を注入するのではなく functional interface の実装を注入する。
  - object を mockup する必要がなくなり、嬉しい。
  - lambda 式なら簡単に mockup ができる。
- Decorator pattern
  - function composition で、任意の関数の前後に処理を差し込める。（※ これ decorator ではなくて Proxy pattern では？？）

# 外部リソースを扱う
`Stream` は `AutoClosable` interface を実装している。これによって、`File#lists` とかで取得した外部リソースを扱う `Stream` であったとしても、trye-with-resource を使って自動的に close することができる。  
Java 8 以前は、`AutoClosable` を実装する class は必ず `close` されなければならないという一般契約だったが、`Stream` は外部リソースを扱うか否かにかかわらず `AutoClosable` を実装した class である -> Java 8 以降は `AutoClosable` の契約が変わっており、必ず `close` されなければならないわけではなく、`close` される可能性がある、というものに変更されている。

## execute around method pattern
Smalltalk 時代からあるデザインパターンのひとつ。[これ](https://www.dontpanicblog.co.uk/2020/11/28/execute-around-idiom-in-java/) がそこそこわかりやすいかも。  
つまり、今回でいえば `FileWriter` で何かを execute するときに、高階関数を導入して、`Consumer<FileWriter>` みたいな操作を外から受け取って、その前後に何か（今回で言えば `FileWriter#close`）を挟み込む、みたいなやつ。DI 的というか、Strategy pattern っぽいというか、Proxy pattern っぽいというか、まあそんな感じ。パターンというよりかは実装手法に近い感じかも。  
これによって、例えば `Closable` の instance を使うときに開発者が `close` し忘れるなどの問題が解決する。

# 「遅延させる」ということ

## Singleton pattern
```java
class Foo {

  private Supplier<Foo> foo = Foo::createAndCache();
  
  private Foo() {
  }
  
  public Foo getInstance() {
    return foo.get();
  }
  
  private synchronized Foo createAndCache() {
    class FooFactory implements Supplier<Foo> {
      private final Foo fooInstance = new Foo();
      public Foo get() { return fooInstance; }
    }
    
    if(!FooFactory.class.isInstance(foo)) {
      foo = new FooFactory();
    }
    
    return foo.get();
  }
  
}
```

## 無限 Stream
```java
  Stream.iterate(2, Primes::smallestPrimeGreaterThanOrEqualTo)
      .limit(lim)
      .toList();
```
みたいな。

# 再帰の最適化
前の章で見た無限 `Stream` を応用すると、末尾再帰を一般化できる。
```java
class Math {

  static int factorial(int num) {
    return factorial(1, num).invoke().intValue();
  }

  private static TailCall<Integer> factorial(int fac, int num) {
    if(num==1) return done(fac);
    else call(() -> factorial(fac*num, num-1));
  }
  
}
```
```java
@FunctionalInterface
interface TailCall<T> {

  TailCall<T> apply();
  default boolean isComplete() { return true; };
  default T result() { throw new UnsupportedOperationException("not complete"); }
  default T invoke() {
    return Stream.iterate(this, TailCall::apply)
        .filter(TailCall::isComplete)
        .findFirst()
        .get()
        .result();
  }
  
}
```
```java
class TailCalls {

  static <T> TailCall<T> done(T t) {
    return new TailCall<T>{
      @Override boolean isComplete() { return true; }
      @Override T result() { return t; }
      @Override TailCall<T> apply() { throw new UnsupportedOperationException("already complete"); }
    }
  }
  
  static <T> TailCall<T> call(TailCall<T> next) { return next; }
  
}
```

※ 多分 Scala のトランポリンと同じ話。

# ラムダ式で合成
# すべてをまとめて
