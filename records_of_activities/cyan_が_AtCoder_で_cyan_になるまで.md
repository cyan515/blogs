# cyan が AtCoder で cyan になるまで

<html>
  <head>
    <link rel="stylesheet" href="https://cyan515.github.io/blogs/records_of_activities/css/cyan.css" type="text/css">
  </head>
  <body>
  </body>
</html>

## この記事に書いてあること

![](./images/cyan_が_AtCoder_で_cyan_になるまで/rating_graph.png)

レートのグラフを見ればわかる通り、2021年の夏から2023年の頭までコンテストに出てませんでした。精進もほぼしておらず、実質休止期間です。

**復帰して以降** について、
- 環境の整備
- 解いた問題
- 学んだこと
- 学ばなかったこと

を書きます。ちなみに **言語は C++** を使っています。

なんで休止以前を省くかって言うと、あんま意味なさそうだからです。

この辺も別の記事でそのうち話せればと思いますが、2021年に入緑しているものの、大した知識はなかったです。

覚えている範囲だと、学んでいたのは BFS、DFS、二分探索、尺取法、imos法、ダイクストラ法 とかそんな感じだったと思います。学んでいたと言っても、触れたことがある程度だったと思います。

[difficultyが年間50くらい厳しくなってる](https://twitter.com/chokudai/status/1665714185320419328)という話もあるらしく、休止前の話はレベル感を考えてもあまりアテにできないかなと思っております。緑になれたのも、ABC-C までの早解きがそこそこ得意だったからというだけですし。

そんなわけで、休止前の話はまた別の機会に。

## 環境の整備
### コーディング環境
実は休止期間前までは AtCoder のコードテストしか使ってませんでした。復帰して1か月ぐらいでしたかね、なんとなく「プログラマとして飯食ってるのに手元に環境構築もできないのヤバくないか？」という不安もあり、ローカル環境の整備をしようということになりました。具体的にやったことは、
- VSCode の導入
- WSL の導入
- ACL の導入

です。

構築に当たっては [こちら](https://iconcreator.hatenablog.com/entry/2021/09/19/200000) に大変お世話になりました。コンピュータへの理解よわよわマンとしては1から10まで説明してくれるこの記事が非常にわかりやすくありがたかった記憶があります（それでもトラブってある程度手間取りましたが……）。

breakpoint を用いた debug は業プロでもよくやりますし、これできるようになったのが一番嬉しかったかもしれないですね。あとはシンタックスハイライトとか、インデントの設定できるとか、補完が効くとか、まあそんなぐらいです。

### ブラウザ プラグイン
[AtCoder Easy Test](https://greasyfork.org/en/scripts/433152-atcoder-easy-test-v2) と [ac-predictor](https://greasyfork.org/en/scripts/369954-ac-predictor) を入れました。

前者に関しては atcoder-tools とか atcoder-cli & online-judge-tools を使ってもいいのでしょうけど、現状がそこそこ快適なのでなおざりにしております……

### テンプレート整備
休止前は
```cpp
#include <bits/stdc++.h>
using namespace std;
```
しか使っていませんでした。

今は
```cpp
#include <bits/stdc++.h>
#include <atcoder/all>
using namespace std;
using namespace atcoder;
using ll = long long;
using mint = modint998244353;
const int INF = 1001001001;
const ll LINF = 3001001001001001001;
const int MOD = 998244353;
#define reps(i, a, n) for (ll i = (a); i < (ll)(n); ++i)
#define rep(i, n) reps(i, 0, n)
#define all(a) (a).begin(), (a).end()
template<typename T> bool chmin(T& a, T b){if(a > b){a = b; return true;} return false;}
template<typename T> bool chmax(T& a, T b){if(a < b){a = b; return true;} return false;}
template <typename T> istream &operator>>(istream &is, vector<T> &v) {for (T &in : v)is >> in;return is;}
```
を使ってます。`ll` と `rep` は特に使用頻度が高いです。

## 解いた問題
復帰後～入水までの間に解いた問題の内、difficulty が茶色以上のものを抽出しました。精進の指針の一端でも担えればと思います。
<div class="details-sample-01">
    <div class="details-wrap">

        <details>
            <summary>
                <span class="summary-text">2023-03</span>
                <span class="summary-icon" aria-hidden="true">
                    <svg class="open-icon" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M12 6v12m6-6H6" />
                    </svg>
                    <svg class="close-icon" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M18 12H6" />
                    </svg>
                </span>
            </summary>
            <div class="details-text">    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc293/tasks/abc293_d">D. Tying Rope</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc253/tasks/abc253_c">C. Max - Min Query</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc253/tasks/abc253_d">D. FizzBuzz Sum Hard</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc294/tasks/abc294_e">E. 2xN Grid</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/sumitrust2019/tasks/sumitb2019_d">D. Lucky PIN</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc295/tasks/abc295_d">D. Three Days Ago</a><br/>

            </div>
        </details>


        <details>
            <summary>
                <span class="summary-text">2023-04</span>
                <span class="summary-icon" aria-hidden="true">
                    <svg class="open-icon" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M12 6v12m6-6H6" />
                    </svg>
                    <svg class="close-icon" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M18 12H6" />
                    </svg>
                </span>
            </summary>
            <div class="details-text">    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc296/tasks/abc296_d">D. M<=ab</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc288/tasks/abc288_c">C. Don’t be cycle</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc055/tasks/arc069_a">C. Scc Puzzle</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc277/tasks/abc277_c">C. Ladder Takahashi</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc184/tasks/abc184_c">C. Super Ryuma</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc270/tasks/abc270_c">C. Simple path</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc226/tasks/abc226_c">C. Martial artist</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc267/tasks/abc267_c">C. Index × A(Continuous ver.)</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc287/tasks/abc287_c">C. Path Graph?</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc260/tasks/abc260_c">C. Changing Jewels</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc299/tasks/abc299_d">D. Find by Query</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc300/tasks/abc300_c">C. Cross</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc300/tasks/abc300_d">D. AABCC</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc055/tasks/arc069_a">C. Scc Puzzle</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc276/tasks/abc276_d">D. Divide by 2 or 3</a><br/>

            </div>
        </details>


        <details>
            <summary>
                <span class="summary-text">2023-05</span>
                <span class="summary-icon" aria-hidden="true">
                    <svg class="open-icon" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M12 6v12m6-6H6" />
                    </svg>
                    <svg class="close-icon" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M18 12H6" />
                    </svg>
                </span>
            </summary>
            <div class="details-text">    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc220/tasks/abc220_d">D. FG operation</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc292/tasks/abc292_e">E. Transitivity</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc268/tasks/abc268_c">C. Chinese Restaurant</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/m-solutions2020/tasks/m_solutions2020_d">D. Road to Millionaire</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc257/tasks/abc257_c">C. Robot Takahashi</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc230/tasks/abc230_d">D. Destroyer Takahashi</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc172/tasks/abc172_d">D. Sum of Divisors</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc241/tasks/abc241_c">C. Connect 6</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/code-festival-2017-qualc/tasks/code_festival_2017_qualc_c">C. Inserting 'x'</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/arc007/tasks/arc007_2">B. 迷子のCDケース</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/arc110/tasks/arc110_b">B. Many 110</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc298/tasks/abc298_c">C. Cards Query Problem</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc245/tasks/abc245_c">C. Choose Elements</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc243/tasks/abc243_c">C. Collision 2</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc264/tasks/abc264_d">D. "redocta".swap(i,i+1)</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc258/tasks/abc258_c">C. Rotation</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abl/tasks/abl_c">C. Connect Cities</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc252/tasks/abc252_c">C. Slot Strategy</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc261/tasks/abc261_d">D. Flipping and Bonus</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/jsc2019-qual/tasks/jsc2019_qual_b">B. Kleene Inversion</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc064/tasks/abc064_d">D. Insertion</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/agc040/tasks/agc040_a">A. ><</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/code-festival-2015-morning-easy/tasks/cf_2015_morning_easy_b">B. ヘイホー君と置き換え</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/arc125/tasks/arc125_a">A. Dial Up</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc259/tasks/abc259_c">C. XX to XXX</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc301/tasks/abc301_d">D. Bitmask</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc283/tasks/abc283_d">D. Scope</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc291/tasks/abc291_e">E. Find Permutation</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc298/tasks/abc298_d">D. Writing a Numeral</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc240/tasks/abc240_c">C. Jumping Takahashi</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc297/tasks/abc297_e">E. Kth Takoyaki Set</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc302/tasks/abc302_c">C. Almost Equal</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc302/tasks/abc302_d">D. Impartial Gift</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc302/tasks/abc302_e">E. Isolation</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc302/tasks/abc302_c">C. Almost Equal</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/arc126/tasks/arc126_a">A. Make 10</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc247/tasks/abc247_d">D. Cylinder</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc285/tasks/abc285_d">D. Change Usernames</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc284/tasks/abc284_d">D. Happy New Year 2023</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc286/tasks/abc286_c">C. Rotate and Palindrome</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc303/tasks/abc303_c">C. Dash</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc303/tasks/abc303_d">D. Shift vs. CapsLock</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc217/tasks/abc217_d">D. Cutting Woods</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/agc012/tasks/agc012_a">A. AtCoder Group Contest</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/arc154/tasks/arc154_b">B. New Place</a><br/>

            </div>
        </details>


        <details>
            <summary>
                <span class="summary-text">2023-06</span>
                <span class="summary-icon" aria-hidden="true">
                    <svg class="open-icon" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M12 6v12m6-6H6" />
                    </svg>
                    <svg class="close-icon" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M18 12H6" />
                    </svg>
                </span>
            </summary>
            <div class="details-text">    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/arc104/tasks/arc104_b">B. DNA Sequence</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc234/tasks/abc234_d">D. Prefix K-th Max</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc304/tasks/abc304_e">E. Good Graph</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc304/tasks/abc304_d">D. A Piece of Cake</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc242/tasks/abc242_c">C. 1111gal password</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc250/tasks/abc250_d">D. 250-like Number</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc258/tasks/abc258_d">D. Trophy</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc182/tasks/abc182_d">D. Wandering</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc272/tasks/abc272_d">D. Root M Leaper</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc245/tasks/abc245_d">D. Polynomial division</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc287/tasks/abc287_d">D. Match or Not</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc305/tasks/abc305_d">D. Sleep Log</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc166/tasks/abc166_d">D. I hate Factorization</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc258/tasks/abc258_b">B. Number Box</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc069/tasks/arc080_b">D. Grid Coloring</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc250/tasks/abc250_c">C. Adjacent Swaps</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc249/tasks/abc249_c">C. Just K</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc217/tasks/abc217_e">E. Sorting Queries</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc249/tasks/abc249_d">D. Index Trio</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc306/tasks/abc306_d">D. Poisonous Full-Course</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc306/tasks/abc306_e">E. Best Performances</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc240/tasks/abc240_d">D. Strange Balls</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc005/tasks/abc005_3">C. おいしいたこ焼きの売り方</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc226/tasks/abc226_d">D. Teleportation</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc209/tasks/abc209_d">D. Collision</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc307/tasks/abc307_d">D. Mismatched Parentheses</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc307/tasks/abc307_e">E. Distinct Adjacent</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc307/tasks/abc307_c">C. Ideal Sheet</a><br/>

            </div>
        </details>


        <details>
            <summary>
                <span class="summary-text">2023-07</span>
                <span class="summary-icon" aria-hidden="true">
                    <svg class="open-icon" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M12 6v12m6-6H6" />
                    </svg>
                    <svg class="close-icon" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M18 12H6" />
                    </svg>
                </span>
            </summary>
            <div class="details-text">    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc308/tasks/abc308_d">D. Snuke Maze</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc308/tasks/abc308_c">C. Standings</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc308/tasks/abc308_e">E. MEX</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc308/tasks/abc308_f">F. Vouchers</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc254/tasks/abc254_e">E. Small d and k</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc257/tasks/abc257_d">D. Jumping Takahashi 2</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/indeednow-quala/tasks/indeednow_2015_quala_3">C. 説明会</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/arc162/tasks/arc162_a">A. Ekiden Race</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc254/tasks/abc254_c">C. K Swap</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc232/tasks/abc232_d">D. Weak Takahashi</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc256/tasks/abc256_c">C. Filling 3x3 array</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc237/tasks/abc237_d">D. LR insertion</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc256/tasks/abc256_d">D. Union of Interval</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc278/tasks/abc278_d">D. All Assign Point Add</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc231/tasks/abc231_d">D. Neighbors</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc153/tasks/abc153_e">E. Crested Ibis vs Monster</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc149/tasks/abc149_d">D. Prediction and Restriction</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc265/tasks/abc265_d">D. Iroha and Haiku (New ABC Edition)</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc309/tasks/abc309_d">D. Add One Edge</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc309/tasks/abc309_e">E. Family and Insurance</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc309/tasks/abc309_d">D. Add One Edge</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc310/tasks/abc310_d">D. Peaceful Teams</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc310/tasks/abc310_e">E. NAND repeatedly</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc189/tasks/abc189_d">D. Logical Expression</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc243/tasks/abc243_d">D. Moves on Binary Tree</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc221/tasks/abc221_d">D. Online games</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc277/tasks/abc277_d">D. Takahashi's Solitaire</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc019/tasks/abc019_3">C. 高橋くんと魔法の箱</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc126/tasks/abc126_d">D. Even Relation</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc176/tasks/abc176_e">E. Bomber</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/arc006/tasks/arc006_2">B. あみだくじ</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc235/tasks/abc235_d">D. Multiply and Rotate</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/digitalarts2012/tasks/digitalarts_1">A. C-Filter</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc026/tasks/abc026_c">C. 高橋君の給料</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/arc042/tasks/arc042_a">A. 掲示板</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc147/tasks/abc147_d">D. Xor Sum 4</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc311/tasks/abc311_c">C. Find it!</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc311/tasks/abc311_d">D. Grid Ice Floor</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc311/tasks/abc311_e">E. Defect-free Squares</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc311/tasks/abc311_c">C. Find it!</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc311/tasks/abc311_e">E. Defect-free Squares</a><br/>
    <font style="color: rgb(0,0,225);" size="6">●</font> <a href="https://atcoder.jp/contests/abc203/tasks/abc203_d">D. Pond</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc181/tasks/abc181_d">D. Hachi</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc015/tasks/abc015_3">C. 高橋くんのバグ探し</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc200/tasks/abc200_d">D. Happy Birthday! 2</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc232/tasks/abc232_c">C. Graph Isomorphism</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc177/tasks/abc177_d">D. Friends</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc186/tasks/abc186_d">D. Sum of difference</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc128/tasks/abc128_c">C. Switches</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc312/tasks/abc312_c">C. Invisible Hand</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc312/tasks/abc312_d">D. Count Bracket Sequences</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc215/tasks/abc215_d">D. Coprime 2</a><br/>

            </div>
        </details>


        <details>
            <summary>
                <span class="summary-text">2023-08</span>
                <span class="summary-icon" aria-hidden="true">
                    <svg class="open-icon" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M12 6v12m6-6H6" />
                    </svg>
                    <svg class="close-icon" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M18 12H6" />
                    </svg>
                </span>
            </summary>
            <div class="details-text">    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc312/tasks/abc312_f">F. Cans and Openers</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc286/tasks/abc286_d">D. Money in Hand</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc246/tasks/abc246_d">D. 2-variable Function</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/caddi2018b/tasks/caddi2018_a">C. Product and GCD</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/tenka1-2019-beginner/tasks/tenka1_2019_c">C. Stones</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc262/tasks/abc262_d">D. I Hate Non-integer Number</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/jsc2021/tasks/jsc2021_d">D. Nowhere P</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc313/tasks/abc313_c">C. Approximate Equalization 2</a><br/>
    <font style="color: rgb(0,0,225);" size="6">●</font> <a href="https://atcoder.jp/contests/abc313/tasks/abc313_d">D. Odd or Even</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc188/tasks/abc188_d">D. Snuke Prime</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc165/tasks/abc165_c">C. Many Requirements</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc267/tasks/abc267_d">D. Index × A(Not Continuous ver.)</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc275/tasks/abc275_d">D. Yet Another Recursive Function</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc269/tasks/abc269_d">D. Do use hexagon grid</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc255/tasks/abc255_d">D. ±1 Operation 2</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc213/tasks/abc213_d">D. Takahashi Tour</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc144/tasks/abc144_d">D. Water Bottle</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc218/tasks/abc218_d">D. Rectangles</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc279/tasks/abc279_d">D. Freefall</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc248/tasks/abc248_d">D. Range Count Query</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc233/tasks/abc233_d">D. Count Interval</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc229/tasks/abc229_d">D. Longest X</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc225/tasks/abc225_d">D. Play Train</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc212/tasks/abc212_d">D. Querying Multiset</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc211/tasks/abc211_d">D. Number of Shortest paths</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc162/tasks/abc162_d">D. RGB Triplets</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc314/tasks/abc314_d">D. LOWER</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc136/tasks/abc136_d">D. Gathering Children</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc248/tasks/abc248_c">C. Dice Sum</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc275/tasks/abc275_c">C. Counting Squares</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc277/tasks/abc277_c">C. Ladder Takahashi</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc199/tasks/abc199_c">C. IPFL</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc171/tasks/abc171_e">E. Red Scarf</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc264/tasks/abc264_c">C. Matrix Reducing</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc287/tasks/abc287_e">E. Karuta</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc182/tasks/abc182_e">E. Akari</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc077/tasks/arc084_a">C. Snuke Festival</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc035/tasks/abc035_c">C. オセロ</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc045/tasks/arc061_a">C. Many Formulas</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc099/tasks/abc099_c">C. Strange Bank</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc102/tasks/arc100_a">C. Linear Approximation</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/panasonic2020/tasks/panasonic2020_d">D. String Equivalence</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc129/tasks/abc129_d">D. Lamp</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc194/tasks/abc194_e">E. Mex Min</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc219/tasks/abc219_d">D. Strange Lunchbox</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc142/tasks/abc142_e">E. Get Everything</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc239/tasks/abc239_e">E. Subtree K-th Max</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc053/tasks/arc068_b">D. Card Eater</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc031/tasks/abc031_c">C. 数列ゲーム</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc216/tasks/abc216_e">E. Amusement Park</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/arc051/tasks/arc051_a">A. 塗り絵</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/arc017/tasks/arc017_2">B. 解像度が低い。</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/arc054/tasks/arc054_a">A. 動く歩道</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/arc008/tasks/arc008_2">B. 謎のたこ焼きおじさん</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc024/tasks/abc024_c">C. 民族大移動</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc028/tasks/abc028_d">D. 乱数生成</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc040/tasks/abc040_c">C. 柱柱柱柱柱</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc030/tasks/abc030_c">C. 飛行機乗り</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc039/tasks/abc039_d">D. 画像処理高橋君</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc127/tasks/abc127_d">D. Integer Cards</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc125/tasks/abc125_c">C. GCD on Blackboard</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc079/tasks/abc079_d">D. Wall</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc012/tasks/abc012_4">D. バスと避けられない運命</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc019/tasks/abc019_4">D. 高橋くんと木の直径</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc032/tasks/abc032_c">C. 列</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc049/tasks/arc065_a">C. Daydream</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc051/tasks/abc051_c">C. Back and Forth</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc130/tasks/abc130_d">D. Enough Array</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc315/tasks/abc315_e">E. Prerequisites</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc006/tasks/abc006_3">C. スフィンクスのなぞなぞ</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc048/tasks/arc064_a">C. Boxes and Candies</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc057/tasks/abc057_c">C. Digits in Multiplication</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc076/tasks/abc076_c">C. Dubious Document 2</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc075/tasks/abc075_c">C. Bridge</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc052/tasks/arc067_b">D. Walk and Teleport</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc070/tasks/abc070_d">D. Transit Tree Path</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc071/tasks/arc081_b">D. Coloring Dominoes</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc073/tasks/abc073_d">D. joisino's travel</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc094/tasks/arc095_b">D. Binomial Coefficients</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc097/tasks/arc097_a">C. K-th Substring</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc097/tasks/arc097_b">D. Equals</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc002/tasks/abc002_4">D. 派閥</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc109/tasks/abc109_d">D. Make Them Even</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc088/tasks/abc088_d">D. Grid Repainting</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc090/tasks/arc091_b">D. Remainder Reminder</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc047/tasks/arc063_b">D. An Invisible Hand</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc054/tasks/abc054_c">C. One-stroke Path</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc084/tasks/abc084_c">C. Special Trains</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc084/tasks/abc084_d">D. 2017-like Number</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc172/tasks/abc172_c">C. Tsundoku</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc317/tasks/abc317_c">C. Remembering the Days</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc317/tasks/abc317_d">D. President</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc317/tasks/abc317_e">E. Avoid Eye Contact</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc206/tasks/abc206_d">D. KAIBUNsyo</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc235/tasks/abc235_e">E. MST + 1</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc307/tasks/abc307_c">C. Ideal Sheet</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc268/tasks/abc268_d">D. Unique Username</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc267/tasks/abc267_e">E. Erasing Vertices 2</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc137/tasks/abc137_d">D. Summer Vacation</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc107/tasks/arc101_a">C. Candles</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc274/tasks/abc274_d">D. Robot Arms 2</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc259/tasks/abc259_d">D. Circumferences</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc112/tasks/abc112_d">D. Partition</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc112/tasks/abc112_c">C. Pyramid</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc252/tasks/abc252_d">D. Distinct Trio</a><br/>

            </div>
        </details>


        <details>
            <summary>
                <span class="summary-text">2023-09</span>
                <span class="summary-icon" aria-hidden="true">
                    <svg class="open-icon" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M12 6v12m6-6H6" />
                    </svg>
                    <svg class="close-icon" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M18 12H6" />
                    </svg>
                </span>
            </summary>
            <div class="details-text">    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc134/tasks/abc134_e">E. Sequence Decomposing</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc318/tasks/abc318_c">C. Blue Spring</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc318/tasks/abc318_e">E. Sandwiches</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc318/tasks/abc318_d">D. General Weighted Max Matching</a><br/>
    <font style="color: rgb(192,192,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc318/tasks/abc318_f">F. Octopus</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/arc009/tasks/arc009_2">B. おとぎの国の高橋君</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc319/tasks/abc319_d">D. Minimum Width</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc319/tasks/abc319_c">C. False Hope</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc319/tasks/abc319_e">E. Bus Stops</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc281/tasks/abc281_e">E. Least Elements</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc135/tasks/abc135_d">D. Digits Parade</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc216/tasks/abc216_d">D. Pair of Balls</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc218/tasks/abc218_c">C. Shapes</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc218/tasks/abc218_e">E. Destruction</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc222/tasks/abc222_d">D. Between Two Arrays</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc223/tasks/abc223_d">D. Restricted Permutation</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc236/tasks/abc236_d">D. Dance</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc194/tasks/abc194_d">D. Journey</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc238/tasks/abc238_d">D. AND and SUM</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc320/tasks/abc320_d">D. Relative Position</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc320/tasks/abc320_c">C. Slot Strategy 2 (Easy)</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc320/tasks/abc320_e">E. Somen Nagashi</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc234/tasks/abc234_e">E. Arithmetic Number</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc229/tasks/abc229_e">E. Graph Destruction</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc230/tasks/abc230_e">E. Fraction Floor Sum</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc240/tasks/abc240_e">E. Ranges on Tree</a><br/>
    <font style="color: rgb(0,0,225);" size="6">●</font> <a href="https://atcoder.jp/contests/abc023/tasks/abc023_d">D. 射撃王</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc233/tasks/abc233_e">E. Σ[k=0..10^100]floor(X／10^k)</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc253/tasks/abc253_e">E. Distance Sequence</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc299/tasks/abc299_e">E. Nearest Black Vertex</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc147/tasks/abc147_c">C. HonestOrUnkind2</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc151/tasks/abc151_d">D. Maze Master</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc321/tasks/abc321_c">C. 321-like Searcher</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc321/tasks/abc321_d">D. Set Menu</a><br/>
    <font style="color: rgb(0,0,225);" size="6">●</font> <a href="https://atcoder.jp/contests/abc321/tasks/abc321_e">E. Complete Binary Tree</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc154/tasks/abc154_d">D. Dice in Line</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc161/tasks/abc161_d">D. Lunlun Number</a><br/>
    <font style="color: rgb(0,0,225);" size="6">●</font> <a href="https://atcoder.jp/contests/abc321/tasks/abc321_f">F. #(subset sum = K) with Add and Erase</a><br/>
    <font style="color: rgb(0,0,225);" size="6">●</font> <a href="https://atcoder.jp/contests/abc315/tasks/abc315_f">F. Shortcuts</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc085/tasks/abc085_d">D. Katana Thrower</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc108/tasks/arc102_a">C. Triangular Relationship</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc322/tasks/abc322_e">E. Product Development</a><br/>

            </div>
        </details>


        <details>
            <summary>
                <span class="summary-text">2023-10</span>
                <span class="summary-icon" aria-hidden="true">
                    <svg class="open-icon" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M12 6v12m6-6H6" />
                    </svg>
                    <svg class="close-icon" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M18 12H6" />
                    </svg>
                </span>
            </summary>
            <div class="details-text">    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc322/tasks/abc322_d">D. Polyomino</a><br/>
    <font style="color: rgb(0,0,225);" size="6">●</font> <a href="https://atcoder.jp/contests/abc322/tasks/abc322_f">F. Vacation Query</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc296/tasks/abc296_e">E. Transition Game</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc281/tasks/abc281_d">D. Max Multiple</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc323/tasks/abc323_d">D. Merge Slimes</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc323/tasks/abc323_e">E. Playlist</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc208/tasks/abc208_d">D. Shortest Path Queries 2</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc241/tasks/abc241_d">D. Sequence Query</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc228/tasks/abc228_d">D. Linear Probing</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc233/tasks/abc233_c">C. Product</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc255/tasks/abc255_c">C. ±1 Operation 1</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc230/tasks/abc230_c">C. X drawing</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc324/tasks/abc324_c">C. Error Correction</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc324/tasks/abc324_d">D. Square Permutation</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc324/tasks/abc324_e">E. Joint Two Strings</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc042/tasks/arc058_a">C. Iroha's Obsession</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc055/tasks/arc069_b">D. Menagerie</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc062/tasks/arc074_a">C. Chocolate Bar</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc043/tasks/arc059_b">D. Unbalanced</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc080/tasks/abc080_c">C. Shopping Street</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc120/tasks/abc120_d">D. Decayed Bridges</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc196/tasks/abc196_d">D. Hanjo</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc325/tasks/abc325_c">C. Sensors</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc325/tasks/abc325_e">E. Our clients, please wait a moment</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc325/tasks/abc325_d">D. Printing Machine</a><br/>
    <font style="color: rgb(0,0,225);" size="6">●</font> <a href="https://atcoder.jp/contests/abc325/tasks/abc325_f">F. Sensor Optimization Dilemma</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc134/tasks/abc134_d">D. Preparing Boxes</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc106/tasks/abc106_d">D. AtCoder Express 2</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc176/tasks/abc176_d">D. Wizard in Maze</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc119/tasks/abc119_c">C. Synthetic Kadomatsu</a><br/>
    <font style="color: rgb(0,0,225);" size="6">●</font> <a href="https://atcoder.jp/contests/abc045/tasks/arc061_b">D. Snuke's Coloring</a><br/>
    <font style="color: rgb(0,0,225);" size="6">●</font> <a href="https://atcoder.jp/contests/abc054/tasks/abc054_d">D. Mixing Experiment</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc326/tasks/abc326_d">D. ABC Puzzle</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc326/tasks/abc326_e">E. Revenge of "The Salary of AtCoder Inc."</a><br/>
    <font style="color: rgb(0,0,225);" size="6">●</font> <a href="https://atcoder.jp/contests/abc062/tasks/arc074_b">D. 3N Numbers</a><br/>

            </div>
        </details>


        <details>
            <summary>
                <span class="summary-text">2023-11</span>
                <span class="summary-icon" aria-hidden="true">
                    <svg class="open-icon" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M12 6v12m6-6H6" />
                    </svg>
                    <svg class="close-icon" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M18 12H6" />
                    </svg>
                </span>
            </summary>
            <div class="details-text">    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc327/tasks/abc327_d">D. Good Tuple Problem</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc327/tasks/abc327_e">E. Maximize Rating</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc210/tasks/abc210_d">D. National Railway</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc183/tasks/abc183_e">E. Queen on Grid</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc145/tasks/abc145_d">D. Knight</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc119/tasks/abc119_d">D. Lazy Faith</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc146/tasks/abc146_d">D. Coloring Edges on Tree</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc103/tasks/abc103_d">D. Islands War</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc328/tasks/abc328_d">D. Take ABC</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc328/tasks/abc328_e">E. Modulo MST</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc328/tasks/abc328_f">F. Good Set Query</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc096/tasks/abc096_d">D. Five, Five Everywhere</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc091/tasks/arc092_a">C. 2D Plane 2N Points</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc151/tasks/abc151_e">E. Max-Min Sums</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc178/tasks/abc178_e">E. Dist Max</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc157/tasks/abc157_d">D. Friend Suggestions</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc152/tasks/abc152_d">D. Handstand 2</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc152/tasks/abc152_e">E. Flatten</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc089/tasks/abc089_d">D. Practical Skill Test</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc126/tasks/abc126_e">E. 1 or 2</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc080/tasks/abc080_d">D. Recording</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc100/tasks/abc100_d">D. Patisserie ABC</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc099/tasks/abc099_d">D. Good Grid</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc179/tasks/abc179_d">D. Leaping Tak</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc157/tasks/abc157_e">E. Simple String Queries</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc133/tasks/abc133_d">D. Rain Flows into Dams</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc138/tasks/abc138_d">D. Ki</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc191/tasks/abc191_e">E. Come Back Quickly</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc330/tasks/abc330_d">D. Counting Ls</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc330/tasks/abc330_c">C. Minimize Abs 2</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc330/tasks/abc330_e">E. Mex and Update</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc237/tasks/abc237_e">E. Skiing</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc164/tasks/abc164_d">D. Multiple of 2019</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc140/tasks/abc140_d">D. Face Produces Unhappiness</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc138/tasks/abc138_e">E. Strings of Impurity</a><br/>

            </div>
        </details>


        <details>
            <summary>
                <span class="summary-text">2023-12</span>
                <span class="summary-icon" aria-hidden="true">
                    <svg class="open-icon" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M12 6v12m6-6H6" />
                    </svg>
                    <svg class="close-icon" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M18 12H6" />
                    </svg>
                </span>
            </summary>
            <div class="details-text">    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc264/tasks/abc264_e">E. Blackout 2</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc331/tasks/abc331_e">E. Set Meal</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc331/tasks/abc331_d">D. Tile Pattern</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc331/tasks/abc331_e">E. Set Meal</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc180/tasks/abc180_d">D. Takahashi Unevolved</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc163/tasks/abc163_d">D. Sum of Large Numbers</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc174/tasks/abc174_e">E. Logs</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc156/tasks/abc156_d">D. Bouquet</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc160/tasks/abc160_e">E. Red andgreen Apples</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc269/tasks/abc269_e">E. Last Rook</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc178/tasks/abc178_d">D. Redistribution</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc224/tasks/abc224_d">D. 8 Puzzle on Graph</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc193/tasks/abc193_d">D. Poker</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc332/tasks/abc332_d">D. Swapping Puzzle</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc303/tasks/abc303_e">E. A Gift From the Stars</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc132/tasks/abc132_d">D. Blue and Red Balls</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc167/tasks/abc167_e">E. Colorful Blocks</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc124/tasks/abc124_d">D. Handstand</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc060/tasks/arc073_b">D. Simple Knapsack</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc181/tasks/abc181_e">E. Transformable Teacher</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc333/tasks/abc333_d">D. Erase Leaves</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc333/tasks/abc333_e">E. Takahashi Quest</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc227/tasks/abc227_c">C. ABC conjecture</a><br/>
    <font style="color: rgb(0,0,225);" size="6">●</font> <a href="https://atcoder.jp/contests/abc227/tasks/abc227_d">D. Project Planning</a><br/>
    <font style="color: rgb(0,0,225);" size="6">●</font> <a href="https://atcoder.jp/contests/abc165/tasks/abc165_e">E. Rotation Matching</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc180/tasks/abc180_e">E. Traveling Salesman among Aerial Cities</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc275/tasks/abc275_e">E. Sugoroku 4</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc334/tasks/abc334_b">B. Christmas Trees</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc334/tasks/abc334_c">C. Socks 2</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc334/tasks/abc334_d">D. Reindeer and Sleigh</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc334/tasks/abc334_e">E. Christmas Color Grid 1</a><br/>

            </div>
        </details>


        <details>
            <summary>
                <span class="summary-text">2024-01</span>
                <span class="summary-icon" aria-hidden="true">
                    <svg class="open-icon" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M12 6v12m6-6H6" />
                    </svg>
                    <svg class="close-icon" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M18 12H6" />
                    </svg>
                </span>
            </summary>
            <div class="details-text">    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc153/tasks/abc153_f">F. Silver Fox vs Monster</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc197/tasks/abc197_e">E. Traveler</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc169/tasks/abc169_e">E. Count Median</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc180/tasks/abc180_e">E. Traveling Salesman among Aerial Cities</a><br/>
    <font style="color: rgb(0,0,225);" size="6">●</font> <a href="https://atcoder.jp/contests/abc190/tasks/abc190_e">E. Magical Ornament</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc246/tasks/abc246_e">E. Bishop 2</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc291/tasks/abc291_f">F. Teleporter and Closed off</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc292/tasks/abc292_f">F. Regular Triangle Inside a Rectangle</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc260/tasks/abc260_d">D. Draw Your Cards</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc170/tasks/abc170_d">D. Not Divisible</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc166/tasks/abc166_e">E. This Message Will Self-Destruct in 5s</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc174/tasks/abc174_c">C. Repsept</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc278/tasks/abc278_e">E. Grid Filling</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc276/tasks/abc276_e">E. Round Trip</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc277/tasks/abc277_e">E. Crystal Switches</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc192/tasks/abc192_e">E. Train</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc284/tasks/abc284_e">E. Count Simple Paths</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc286/tasks/abc286_e">E. Souvenir</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc198/tasks/abc198_e">E. Unique Color</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc188/tasks/abc188_e">E. Peddler</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc179/tasks/abc179_e">E. Sequence Sum</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/arc109/tasks/arc109_b">B. log</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc335/tasks/abc335_c">C. Loong Tracking</a><br/>
    <font style="color: rgb(128,64,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc335/tasks/abc335_d">D. Loong and Takahashi</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc146/tasks/abc146_f">F. Sugoroku</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc335/tasks/abc335_e">E. Non-Decreasing Colorful Path</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc159/tasks/abc159_e">E. Dividing Chocolate</a><br/>
    <font style="color: rgb(0,128,0);" size="6">●</font> <a href="https://atcoder.jp/contests/abc305/tasks/abc305_e">E. Art Gallery on Graph</a><br/>
    <font style="color: rgb(0,192,192);" size="6">●</font> <a href="https://atcoder.jp/contests/abc128/tasks/abc128_d">D. equeue</a><br/>

            </div>
        </details>
</div></div>

### 精進で意識していたこと
前述の通り、解く速度に関してはそんなに課題を感じていなかったので、とにかく解ける問題を増やす方向で考えていました。方針が見えなくても、なんとなく思考が進む限り、どれだけ短くとも30分-1時間ほどは考えていたと思います。

特に適正 difficulty よりも高い問題の内、行けそうで行けない、でもちょっと行けそう、みたいな問題は数日間頭の中に置いておくこともありました。途中で、まったくどん詰まりになったら解説を見ます。
  
そのとき、解説に書いてある解法が頭をかすりもしていなかった場合、それを新たに武器として取り入れるだけなので、話は割と単純です。その解法に関する知識をｇｇるなり何なりして、取り入れます。次回から考察時に選択肢として頭の片隅に置いておけるようになってさえいればよいです。
  
大変なのは、その解法が頭に一旦浮かんだにもかかわらず、その方針で詰めずに捨ててしまった場合です。なぜその方針を捨ててしまったのかを顧みる必要があります。ex. 計算量の見積りを間違えた、正当性の証明ができなかった、何となくダメそうだから捨てた、等々。
  
そしてその原因が、問題文の誤読や勘違いによるものであればまだいいのですが、アルゴリズムやデータ構造に関して何らかの勘違いをしていた場合、ちゃんと矯正する必要があります。これまたｇｇるなり何なりして、当該アルゴリズム/データ構造のお気持ちをちゃんと理解する方向で頭を使います。
  
100% の理解が無理でも、最悪そのアルゴリズム/データ構造の各操作の計算量がいくつなのか/どのようなことが実現できるのかぐらいは理解するようにしてました。

## 学んだこと
### アルゴリズム
- 順列全列挙
- トポロジカルソート
- 区間スケジューリング
- 繰り返し二乗法
- 二次元累積和
- Union Find
- 半分全列挙
- 三分探索
- （遅延評価）セグ木
- クラスカル法
- ワーシャルフロイド法
- SCC
  
他にもありそうな気がしますが、覚えてる範囲だとこれぐらいです。

### 実装手法
- めぐる式二分探索
- `upper_bound` `lower_bound` による二分探索
- lambda 式による再帰
- ゲーム系の DP とかをメモ化再帰で書くやつ

### その他概念とか
- グラフの頂点倍加
- 調和級数
- 群論（ちょっとだけ）
- functional graph
- 期待値 DP
- 期待値 mod
- 確率 DP
- 確率 mod
- bit DP

### ライブラリ化したもの
学んだアルゴリズムも踏まえて、手元にライブラリとして置いたものを紹介します。
- 基数変換
- ランレングス圧縮
- [オーバーフロー検出](https://mycode.rip/check-overflow-in-cpp) （あんまり要らないかも？）
- [繰り返し二乗法によるべき乗の計算](https://algo-logic.info/calc-pow/)
- [部分文字列で使う `calcNext`](https://qiita.com/drken/items/a207e5ae3ea2cf17f4bd)
- combination
- ダイクストラ法
- エラトステネスの篩
- トポロジカルソート
  
他にも、BFS、DFS、めぐる式二分探索 なども一時期ライブラリ化していましたが、水色になる頃には何の苦労もなくその場で書けるようになっていたので、捨ててしまってました。

### ACL で使えるようになったもの
- `dsu`
- `inv_mod`
- `segtree`
- `lazy_segtree`
- `scc_graph`

## 学ばなかったこと
改めて文字に起こしてみると、知らないことだらけですね。「今のところ困ったことがない」と言っているものに関しては、単純に自分の精進不足も大いにあると思います……。

### 全然わからないもの
- フロー
- 平方分割
- 平面走査
- FFT
- Trie
- カタラン数
- grundy 数
- 二部マッチング
- 最小カット
- 行列累乗

### 何ができるかなんとなく知ってるけど今のところできなくて困ったことがないもの
- ローリングハッシュ
- ベルマンフォード法
- 座標圧縮

### 代替手段が存在して今のところ困ったことがないもの
- Binary Indexed Tree
- プリム法

### 学ぼうとしたけどわからなくて一旦諦めたもの
- ダイクストラ法のポテンシャル
- 全方位木 DP
- Z algorithm

## 水色になった今、何をやっているか
特に変わったことをやっているわけでもないのですが、水 diff 埋めを積極的にやるようになりました。AtCoder Problems の heat map を見てみるとこんな感じです。
![](./images/cyan_が_AtCoder_で_cyan_になるまで/heat_map.png)

あと手元のライブラリが若干増えており、
- [重み付き Union Find](https://zenn.dev/reputeless/books/standard-cpp-for-competitive-programming/viewer/weighted-union-find)
- [ロールバック可能 Union Find](https://atcoder.jp/contests/abc328/submissions/47458831)
- [拡張 GCD](https://qiita.com/drken/items/b97ff231e43bce50199a)

あたりを窃盗しました。使うこと自体はそんなに多くないですが、持ってると貼るだけがたまに発生します。

## おわり
良い締めが思いつかないです。青目指して？気長にがんばろうと思います。まあ、そんな感じです。  
ありがとうございました。

[トップへ戻る](https://cyan515.github.io/blogs/)
