# 2302

# 198E Unique Color  diff 1161

解答遷移 TLE WA AC
計測していない

備考

➀ 思考

パスなので dfs ? しかし最短パス = 最短経路なので bfs か～ ⇒ これまでの経路で見た色の集合を管理しながら dfs を実装。また、集合に要素を追加する際、全ての探索済集合が操作されてしまわないようにコピーする必要があると気づく ⇒ TLE ⇒ コピーすると計算量が最悪 O(N^2) (1+2+3+...N) となってしまうことに気が付く 

なんとか探索済みの色を工夫して管理できないか考えたが難しい ⇒ 木であることに注目すると、dfs で探索した経路が必ず最短経路になることに気が付く。これならば帰りがけに探索済みの色を操作できるので勝った ⇒ WA ⇒ 帰りがけで必ず探索済みリストからその色を削除してしまうと、それまでの経路でその色が登場している場合に誤りが生じることに気が付く　⇒ 個数を管理して、0 になれば削除する処理に修正して AC

➁ 感想

木の場合 dfs でも最短経路を求められること。dfs はパス問題(経路記憶問題)に強いことを理解する (bfs では同時に複数の経路を処理する関係で経路記憶に強くない)

# ☆ 216E  Amusement Park   diff  1084  別解を思いつきたい

解答遷移 TLE AC

計測なし

備考

➀　思考

素直に優先度付きキューで最大値を管理して、それを-1して入れなおす処理で TLE (Kの制約より) ⇒ 二分探索っぽい雰囲気を感じながらも実装方法がわからない ⇒ 最大値の乗り物には、次に大きな値の乗り物より楽しさが大きい間乗り続ける。そしてこれらが同値となったタイミングでその乗り物と交互に、そのまた次に大きな値の乗り物より楽しさが大きい間乗り続ける。したがって楽しさが大きい乗り物から順に、次の楽しさの位置まで O(1) で楽しさ総和を加算する処理を繰り返せばよいと考えた。これは全体で O(N) なので十分高速と判断。

なお、途中で K　を超える場合には、⌊ 残数/最大値を持つ乗り物の数 ⌋ で最大値を持つ乗り物すべてに乗れる回数を、残数 mod 最大値 を持つ乗り物の数 で最後に乗れる回数を求めることで、計算を行った

➁ 別解

最大値 m 以上の乗り物すべてに K 回で乗れるか 二分探索することで、限界直前の楽しさを求めることができる。あとは、その楽しさ以上の乗り物にこの値になるまで乗り続け、限界値に 残数回乗れば 答えが求められる。計算量は全体で O(N logK) となって十分高速


# 184D increment of coins  diff 1276

解答遷移 AC

計 1時間程度(A～D は解けそう)

備考

➀ 思考






# 183E Queen on Grid  diff 1288

解答遷移　AC

計 56:25

備考

➀ 思考



# 0202

# ☆ 164D Multiple of 2019  diff　

降参

備考
　
➀ 思考

連続区間ではあるが、単調性はないので尺取り法的には考えられない。片側固定していろいろ考えたがわからず降参

➁ 解法

20191111 = 20190000 + 1111　⇒ 20191111 = 1111 (mod 2019) が成立することに注目。つまり、区間の左端から末端までで成す整数と、区間の右端+1 の位置から末端までで成す整数 をそれぞれ 2019 で割った余りが等しければ その区間が条件を満たすことになる。したがって、右端側から余りを計算していき、同じ余りが2つ以上存在するものを 2つ選ぶ組み合わせを求めればよい。計算書は O(N) ただし、巨大整数を生成することを考慮して pow を使う必要があることに注意

③ 定石

連続区間へのアプローチの定石として、「 片側固定 」だけでなく 「 累積差分 」を理解する必要がある。

ある区間 [a,b] を、[1,b] と [1,a-1] の差分で解釈するということである。累積和は これの和 をとった ver ということである。



# 186D Sum of difference  diff 436   2回目

解答遷移 AC

計 06:55

備考

➀ 思考

絶対値の差を考えやくするために A を降順にソート。これによって答えは A0-A1 + A0-A1 + ... A0-AN + A1-A2 +... となるので、末尾側からの累積和を取ればよいと判断


# 182D Wandering  diff 701  2回目

解答遷移 AC

計 18:43

備考

➀　思考

次の移動先は累積和で簡単に求めることができるが、途中でそれよりも先に進んでいるケースを考えなければならない。これには次の移動先に至るまでに進める最大の差を持って置けば、現在地 + その値　で移動できる最大値を更新できる。したがって、1, 現在地 2, 現在の移動差分の最大値 を管理する必要があることが分かった。また、現在地の更新のためには 3,現在の移動差分 も管理する必要がある。⇒ 移動差分は A の累積和で求めて、都度最大値を更新することで移動差分の最大値も同時に求められる。移動差分で現在地を更新しながら、移動差分の最大値と現在地の和で 求めるべき最大値を求めればよいと判断

# 163D Sum of Large Numbers	  diff 960  2回目

解答遷移 AC

計 11:29

備考

➀　思考

個数で和が異なこと、K個選んだ和は (+1+2+...K-1)　～ (N-K-1 + ... N-1 + N) までの連続値となることに注目すれば種類が求まると判断



# Segment Tree 勉強

・参考

https://qiita.com/AkariLuminous/items/32cbf5bc3ffb2f84a898#36-%E5%AE%9F%E8%A1%8C%E9%80%9F%E5%BA%A6%E3%81%AE%E6%94%B9%E5%96%84

⇒ 完全二分木(頂点数が 2^N) でテーブルを作る実装。これをメインに作成した

https://maspypy.com/segment-tree-%E3%81%AE%E3%81%8A%E5%8B%89%E5%BC%B71


・ 単位元 と 結合法則

最小問題における　∞ , 和演算における 0 , 積演算における 1 のように、演算に含めても結果が変化しない価のことを 単位元 e と呼ぶ

結合法則は演算の順番 例) 1+2+3 ⇔ 1+(2+3) 。 セグメントツリーではこれが成立している前提。なお、1+3+2 のような要素の順序の変更が結果に影響しないルールは 交換法則である。混同注意。

・データ構造

一次元リストで表現した完全二分木。サイズは 対象配列サイズ: N ≦ 2^a のときに、 2^(a+1) (1-indexexに調整するために頂点数 +1とする)

最下層は (0 + 最下層サイズ) - indexed である。

また、op,e はそれぞれ関数で定義する必要がある。

・できること

➀ 一点更新

![image](https://user-images.githubusercontent.com/109026838/216410049-1abd6a29-d6d5-4063-993c-79684c79b7ec.png)


最下層から、関連する頂点を全て更新。各層で一度更新が行われるので 計算量は O(logN) (層数が logN )

➁ 区間取得

![image](https://user-images.githubusercontent.com/109026838/216399332-b44c0401-2e5e-4d4b-85d5-bf5b67b973dc.png)

最下層から、区間を表現するために最適な頂点を求める。区間の端から内側へ調べていくイメージ。各層で 両端 2頂点のみ操作するので、計算量はO(logN)

[l,r) 、つまり右側半区間を考えているため r が区間に含まれない点に注意が必要。右端頂点が左の子であれば内側に移動するが、これは r が右の子である場合である。したがって、左の子であれば内側に移動する左端と同じ内側移動条件を設定することになる。



# ☆ ACL D Flat Subsequence  diff 1283

降参

備考

➀ 思考

右端から、最も左側に存在する頂点 X に最大何手で移動できるか考えれば良さそう ⇒ A-K ～ A+K の頂点すべてを操作する必要があること、imos 法を使っても毎回累積和を求める必要があることで計算量的に難しい　⇒他の案も見つからず降参

➁ 解法

まずこの問題は LIS(最長増加部分列) の類題である。

===============================================================================================

LIS

・参考

https://ikatakos.com/pot/programming_algorithm/dynamic_programming/longest_common_subsequence

https://qiita.com/drken/items/68b8503ad4ffb469624c#3-lis-%E3%81%AE%E8%A7%A3%E6%B3%951-%E4%BA%8C%E5%88%86%E6%8E%A2%E7%B4%A2-ver

・解法

➀ 前から i番目の値を末尾に持つ部分列の長さ を求める

0 ～ A[i]-1 までの値を末尾に持つ部分列の最大値 +1 でこの値を更新できることを考えると、 1, 前から何番目か 2, 前から i番目の値を末尾に持つ部分列の長さ の情報があれば dp できる。ただし、0 ～ i-1 の区間の最大値を高速に求めるために segment-tree で情報を管理する必要がある。

また、i番目の操作で更新されるのは iの位置の一点のみであり他の位置は更新されないことから、dpテーブルは 1次元で十分である。

⇒ この in-place 化で計算量を大幅に削減できる手法は他でも応用できそうなので、慣れておきたい

※ 追記 230208  251E 解答後

![image](https://user-images.githubusercontent.com/109026838/217298462-95e4f2c7-a949-4da2-9091-61555b33da50.png)




➁ 長さ K となる部分列のうち、その最後の要素の最小値を更新することで最大の部分列の長さを求める。

![image](https://user-images.githubusercontent.com/109026838/216405657-9986a5ec-e738-4376-86c5-d4ee4eb81af0.png)

 

=================================================================================================

つまり、この問題は取得する区間の範囲が [ max(0,A[i]-K) , min(max(A),A[i]+K ) ver になった ISL である。


# 0203

# 185F Range Xor Query  diff 1053

解答遷移 AC

備考

➀　思考

Ti=1 で一点更新, Ti=2 で区間取得なので Segment Tree で管理すれば解けそう ⇒ 最下層が (0+最下層サイズ) -indexed , X,Y が1-indexe であるのでこれを調整して AC 。計算量は全体で O( NlogN ) で十分高速



# ☆281E Least Elements  diff 

⇒ 230215 に書いた

# 0204

# 157E Simple String Queries  diff 1443

解答遷移 WA ⇒ AC

計 1:14:57 +05:00

備考

➀ 思考

一点更新 + 区間取得なので Segment tree で解けそうだが、種類の個数の管理がだるい。種類の削除を上手に表現できる更新関数がよくわからない ⇒ N * 26 のテーブルで i文字目までの文字の個数を管理して累積差分を取る方針では文字の変更が一点更新ではなくなってしまうので、これも難しい。⇒ アルファベットごとにセグメントツリーを作成して i文字目がそのアルファベットかの真偽を管理すれば、更新関数 max() で任意の区間でそのアルファベットが存在するか判定できることを思いつく。計算量も O(NlogN + 26QlogN) で十分高速。 

ただし、文字の入れ替えが生じる際、実際に S を更新しなければならないことに気を付ける。これに 30分以上気付けなかった



➁ 別解

種類を 26進数で管理すれば bit和をとることで区間の種類を更新できる。計算量も (NlogN + 26QlogN)で十分高速

もし素直に種類で管理する場合、和集合をとるために 26回計算を要するので、 O(26NlogN + 26QlogN) で前半部の定数倍が重くて間に合わない。和集合をとる行為が嫌すぎてこれを回避していたが、実際にTLE する


# 0205 

# 215D Coprime 2  diff  736  n回目

解答遷移 TLE TLE AC

計 30 ～ 40 m ? + 10:00

備考

➀　思考

Ai と k の最大公約数をいちいち比較することはできない。そこで、П A にはAに含まれるすべての素因数が含まれることに注目し、これと 1 ～ M の最大公約数を調べればよいと考えた ⇒ しかし、ПA < (10^5)^(10^5) より 計算量が O(M × logПA) では到底間に合わず TLE ⇒ 総積には素因数が重複していることに気づき、これを解消しようと考えたがむずかしかった ⇒ 一旦仕切りなおして考えると、各素因数の倍数を記憶しておき、これと i を比較して一致しないものを求めればよいことに気が付く。素因数の倍数の記憶は エラストテネスの篩 で実行すればよいので計算量は O(M + N√N + AiloglogAi) となって十分高速


# 174E Logs diff 1227

解答遷移 TLE AC

計 21:56 + 05:00

備考

➀　思考

全ての丸太を x 以下にできるか二分探索すればよいと判断。Ai ≧ mid なら que に Ai-mid を格納していく処理で回数を計上する ⇒ TLE これでは O(KlogK) になってしまう ⇒ Ai を切れる回数が 、⌈ Ai/mid ⌉ -1 = (Ai+mid-1)//K -1 = ⌊ (Ai-1)/mid ⌋ ※ であることに気づいて O(NlogK) に修正して AC

※ 境界でこれらが一致することは確認したが、厳密に正しいか不明


# ☆ 198D Send More Money  diff 1224

降参

備考

➀ 思考

![image](https://user-images.githubusercontent.com/109026838/216841998-53e02c66-ed4e-466e-8758-1c0e96949d53.png)

このように N の下の桁からアルファベットを決定していけばよいと考えたが、再帰を実装できなかった。Sの行き来、桁の移動に加えて、帰りがけで忘れる処理が伴うので可能かもだが相当複雑。少なくも現時点では到底時間内に実装できそうになかった。

➁ 解法

アルファベットと数字の組み合わせを全探索する。条件を満たす場合、アルファベットごとに数字が重複しないことからこれらは 10! 通りになることを正確に評価できず、この方針を棄却してしまった(10^10 で無理だな～ と感じた)。➀　と違って、これであれば N が簡単に決定するので判定がめちゃめちゃ楽である。

注意点としては、10! 通りを全探索するために出現文字の種類を 10種に調整する必要がある。適当に ゼロで埋めておき、数字と対応させる処理でスキップすると良いだろう。

さらに、N は非ゼロであることに注意。つまり、最上位桁に 0 は現れない


③ 反省  ～ 解説確認後実装時 ～

初見時の思考やコードを引きづっていたのか、Sを10桁にゼロ埋めしたままにした。これによって、SSで登場文字の種類を管理する際にめちゃくちゃバグってしまった。具体的にはゼロ埋めの影響で必ず SS に0 が含まれる前提で、SSを長さ 10 にする調整を行っていたのだが、これでは adeaaaaaaa,bfghbbbbbb,ccijkccccc など、ゼロ埋めが生じない場合に 11! 通りの全探索を行うようになってしまう。これで TLE を連発した。

また、SS に原因があることにテストで気づいた後も、勝手な思い込みでこの影響が全探索におよぶわけがないと、根拠もなしに断定し原因把握が死ぬほど遅れてしまった。理想実装では計算量に問題がないはずと考えるならば、面倒くさいが 探索回数を count 定数で調べてみるなどしてみよう。


# 0206

# ☆ 251E Takahashi and Animals  diff 1227

解答遷移 RE RE RE WA AC

計 2:34:00 + 20:00

備考

➀　思考

bit 全探索は不可。dp も制約的に無理。回数、金額 で二分探索しようとしたが、条件設定ができそうにない。⇒ ※Ai 払うなら、Ai+1 は払わないで済むことに注目した 配る dfs なら解けそうだと思いつく。ただし純粋な実装では計算量が爆発してしまう。⇒ ここでメモ化再帰を思い出し。これを 2時間かけて実装した。

※ この考えは実は誤っていて WA を食らった。Ai 払ったとしても、Ai+1 を払わないかどうかは全く分からないからである。Ai 払う場合は、i+1 へ、Ai 払わない場合は Ai+2 へ遷移させることが正しい

他にもところどころ ? な部分が多く、初期思考を頑張って言語化する必要はないと判断し省略。整理して納得したものを ➁ に記す



➁ 思考の整理

![image](https://user-images.githubusercontent.com/109026838/217239877-f3e0c9de-e1a4-43f7-885f-9646d95a8c3d.png)

i≦k≦N  番目までの動物への餌やりが完了している状態からは、i−1 番目の動物に餌を与えるために Ai−1 払って  i−1≦k≦N  番目までの動物への餌やりが完了した状態に遷移するか、もしくは Ai−2 払って i−2≦k≦N 番目までの動物への餌やりが完了した状態へ遷移する。

したがって、f(x) = min( f(x+1) , f(x+2) ) + A[x] が成立。ただし、x=N ⇒ A[x] , x=N-1 ⇒ A[x-1] 

ただし、A[1] 払わない場合についても考える必要があるので、これに対応した f_use(x) を作成。

最終的に min( f_use(1) , f_unuse(2)) が最適解

➁' 補足

i≦k≦N  番目までの動物への餌やりが完了している状態 を 必ずA[i] 払っている前提で考えているのが重要。公式解説では、dp[i][0] で Ai-1 払わずに i番目までの餌やりを完了している状態、 dp[i][1] で Ai 払って i番目までの餌やりを完了している状態を定義している。

これがこの問題の核、肝と言える。

③ 別解

1, 前から何番目までの動物に餌を与えたか

2, i 番目までの動物すべてに餌を与える場合の最小値

以上、2つの情報で状態を定義することで、遷移に忠実に状態を更新できるとわかる。(便宜上、遷移方向を本方針と逆にしたが本質は同じ) 

⇒  N^2 サイズ必要か冷静に考えるべき


④ 注意点

・まずメモ化再帰における引数 maxsize は記憶可能数であり、再帰上限ではない。つまり、普通の再帰処理同様、setcursionlimit で上限を設定しなす必要がある。

・こちらも当然ではあるが、再帰なので pypy < python である。



# 0208 

# 241E Putting Candies  diff 1248

解答遷移 AC

計 1:37 :56

備考

➀ 思考

前から探索して、ループを見つければ完了できる問題だと気づく。計算量も O(N) で十分高速 ⇒ 最後の余りの加算処理を +A[i] でなく +i としてサンプルが合わなかった。これに 1時間くらい全く気付かなかった。

ループを成す頂点を記憶する必要があり、連結リストの要領でこれを求めることにした。また、N個でループを成す場合を考慮して、探索は N+1 回行っている。



# 200D Happy Birthday! 2  diff  1217

解答遷移 AC

計 50:26

備考

➀　思考

1, i 2, 和の余り 3, 成す ind の情報で状態を定義した dp で解けそう。和集合で更新することになるがそれでも計算量は O(N^3) で十分高速。A[i] を追加したばかりの状況、つまり j= A[i] でj+A[i] としないように気を付けて AC 

※ 条件設定はわかっていたが、つける場所を間違えて +10分以上かかった

➁ 別解

鳩ノ巣


# 176E Bomber 1204

解答遷移 AC

計 40:34

備考

➀　思考

爆弾が最大の行、かつ最大の列の交点で爆破すべき。このとき交点に爆弾がなければそれぞれの和になるが、爆弾が存在するなら -1個となる。したがって、各行、各列ごとの爆弾野総数の管理 & 各マスの爆弾の存在の管理 ができればよい。 ⇒ マスの総数は 10^10 であるが、爆弾の存在するマスは最高でも M なので、defaultdict 等で爆弾が存在するマスのみを管理する。⇒　あとは 最大行と最大列の組み合わせを全探索して、そのマスに爆弾が存在するかを調べる

計算量は O(max(H,w)log(max(H,w) + M ) : 最大の行と最大列取得のためにソートする必要があり、最大行と最大列の組み合わせの総数は ※ M で抑えられるため。

※ 最大行 n 個 最大列 m 個 の場合、nmマス探索する必要があり、例えば √2 × 10^4 の長さの対角線上に 1個ずつ爆弾が存在する場合、n=10^4,m=10^4 となるためこれでは間に合わない。しかし、nm>M の場合、必ず爆弾が存在しないマスが含まれ打ち切られるので、実質計算量は O(M) で抑えられる。

➁　解法

最大行、列だけほしいので、sortしなくても、予め求めて置いた最大値と一致するか全探索すればよい。これで計算量は O(max(H,W)+ M) でとても軽い


# 0209

# 157D Friend Suggestions diff 1208

解答遷移 AC

計 21:45

備考

➀ 思考

全点間最小距離を求めるには O(N^3) だし、始点全探索 BFS でも O(N^2) で厳しい。⇒ 友達候補 = 友達の友達 - 友達 - (友達の友達 &ブロック関係) で余事象的に求まることに気づく。友達の友達は union-find で求まるし、友達を調べるためには全部で O(M) の探索 で済むし、(友達の友達 &ブロック関係) も全部で O(K) で済むので十分高速に求められる



# ☆ 147D Xor Sum   diff 1205

降参

備考

➀ 思考

sum = and<<1 + xor  (238D) の性質を使えば計算がまとまって累積和的に計算できそうだと考えた。しかしできず、代案もなく降参


➁ 解法

xor を桁ごとに考える意識が必要。自分はできていると思っていたが、まだまだ弱いようだ。(実際、過去門は意外とこれが核の問題が少ない。)

Σ(1≦ d ≦ 60)  {(Ai xor Aj) のうち、下 d桁目に 1が立っている数 ・・➀ × 1<<d } が求めるべき和であると解釈すると、➀ : 0 xor 1 = 1 より、下 d 桁目が 1である A の要素 × 0 の要素 を求めればよい。


# 138E Strings of Impuritydiff 1257　➁ 解法 必ずマスター

解答遷移 WA WA AC

計 31:48 + 10:00

備考

➀ 思考

T を前から順に見て、S のどの位置に移動するかを考える。具体的には、T[i]= c , 現在地 x のとき、x 以降で最初に c が現れる位置を考える。もし、x 以降にそのような位置がなければ ループ回数をインクリメントして、c が最初に現れる位置に移動すればよい。

これを実行するために、S における出現位置を各文字ごとに管理して、これを二分探索することで移動先を求めればよいと考えた。また、S に存在しない文字が Tに含まれる場合は条件を満たすことがないので、これを途中で検出して exit() する。

注意点としては、初期位置を 0 として移動を開始すると、T[0]=S[0] のときの移動が適切でなくなるので、初期位置または index 番号を調整する必要がある。

➀' 補足

最初は、一番最初に S に現れる位置だけ管理すればいいと勘違いした。(1 WA目) 


➁ 別解

i番目以降に移動可能な最小位置をあらかじめ求めておけば二分探索することなく O(1) で移動先を求められる。

ここで、c が i 番目に存在 ⇔ i-1 番目以降に c が最初に現れる位置は i であることに注目して、テーブルを作成する。このとき、i-1 操作を行うために、index 番号の調整が必要な点に気をつける。


# 0210  

# ☆ 270D Stones  diff  1300

降参

備考

➀ 思考

N=10 A= 1 3 4  で貪欲には解けないと分かる。制約的に dp でも解けない ※し困っていたところ、メモ化再帰ならいけると判断。具体的には f(x) : X個からとれる最大値, g(x) : X 未満で最大の A の要素と定義すれば、f(x) = max( a + f( x- g( x-a ) ) )  で遷移を表現できると考えた。X≦N より計算量は O(N × K × logK)) (二分探索する場合でg(x)を求められる場合) となって十分高速

しかし 2WA 。どうやってもわからず降参

➁ 解法

冷静に考えると当然なのだが、青木君が g(X) 個選ぶことが青木君にとっての最適化とは限らない。つまり、青木君も f(X) 個選ぶことで最適化される。したがって、f(x) = X - f(x-a) で遷移を定義すればよい。

③ ※

251E でも同じことを書いているが、横着せずに状態管理に必要な情報をかけ！！！！ 

1, 残り 何個か

2, 残り x 個で何個最大貰えるか

これで 一次元 dp テーブルで十分だとわかるはず。

④ 反省

青木君の考察を間違ってしまったことは100歩譲るとして、遷移を明確にしようとする強い意志が欠落していること(③) がごみ過ぎる。解法を見て青木君も f(x) と理解してからも、この意識がないせいで、 f(x) = x -f(x-a) を導くのにくそ時間かかってる。だめだめ。

俺の意識だけ。手札は揃ってる。あますぎ。絶対解いてやるという気もちがない。燃やす。



# ☆ 261E Many Operations   diff 1261

解答遷移 AC

計 2:00 :11 

備考

➀ 思考

誤解法 1

X or B = B', B' or B = B'  , X or C = C', C' or C = C' の関係性から、同じ操作を通して、A[i]までの出力は常に同じ値をとるものと勘違いしてしまった。ここからこじれて出力を入力することも抜け落ち、こんがらがってしまい、正しく解釈し直すまでにとても時間がかかった

正解

入力を与えたとき、bitごとに 0,1 どちらが返るかを O(1) で求められれば 全体で O(Nlog 2^30)で十分高速に解答できるなと考えた。i+1 番目までの変換結果 = (i 番目までの変換結果 ) を 操作 i+1 で変換した結果　であるので、実現できそう

⇒ 各桁 0,1 で初期化したテーブルを作成。各操作後、入力の各桁の変換結果を求め、出力し入力を更新。

➁ 解法

正解方針は完璧

☆ 異なる入力、同じ操作 では一般的な出力結果を作成し、入力をあてはめていく戦略が有効なことが分かった。

③ 反省

・ 147D の反省を活かしすぐに桁ごとに考えることができた。

・ 一つ一つの検証が遅すぎて、トライ&エラーを繰り返せない現状。

1発で正解を見抜く力  vs  検証力(速度、正確性)   vs デバック力

これらのすべてが足りていない。


# ☆ 225C Calendar Validator  diff 326  n 回目

解答遷移 AC

計 12:50

備考

➀ 思考

左端を中心に考え、この位置からの差分で表現できる値に一致するか + ありえる並びか を判定する

➁ ☆ 

グリッド一致判定問題の典型として、端をまたぐ場合にバグが生じる可能性を考えることを覚えておく。


# 179C A × B +C   diff 283  n 回目

解答遷移 AC

計 09:07

備考

➀ 思考

文字が多すぎてうざいので、とりあえず a 固定。少し悩んで、a × B  ≦ N より、B を満たす正整数は N//a と分かり、このうち最も大きい N//a が  N//a × a = N  を満たすなら c が 0 になるのでこれを数えない計上を行えばよいと判断。

➁ 解法

固定の考えは〇　あとは、不等式で範囲を絞る基本的な考えを抑えたい。c = N - a × B より、1 ≦ N - a × b ≦ N ⇒ 右辺は必ず成立より、1 ≦ b ≦ N/a 


# 176A Takoyaki   diff 17

解答遷移 AC

計 02:23

備考

➀ 思考

(N//X + (if N%X>0 +1 ) ) × T

➁ 解法

➀ は繰り上げ演算。言われるまで気付かないのやばい



# 0211

# 215B log2N   diff 68  n回目

解答遷移 AC

計 02:38

備考

➀ 思考

2^(k-1) < N < 2^k を満たすとき、N(2) が k桁であることに注目し、N(2) の長さ -1 を出力した

# 223C Doukasen  diff 354  n回目

解答遷移 AC

計 18:27

備考

➀ 思考

・ 全体を燃やす時間 = 2 × ( 左から燃える時間 = 右から燃える時間 ) 

より、全体を燃やす時間の半分の時間でどこまで燃やせるかを調べればよいと考えた。





# 226D Teleportation  diff 706  n回目

解答遷移 AC

計 31分

備考

➀ 思考

最初勘違いしてしまったが、任意の点から任意の点までの移動方法の種類が問われている。また、ベクトルが異なる場合は傾きが同じでも別々で考える必要があるので、ベクトルの種類を数える必要がある。したがって始点を全探索して、他の点に既に覚えたベクトルでいけるかを判定。いけない場合にそれを覚える処理を行えばよいと考えた。




# 0212

# 281 C Serect Number  439 diff   n 回目

解答遷移 AC

計 55:44

備考

➀ 思考

苦手な条件を満たすものを数え上げる問題。パスワードを生成し、条件判定して計上。


# Mex Min  diff    2回目( 初 AC ) 

解答遷移 AC

計 37:37

備考

➀　思考

SortedSet で含まれないものを管理する方針だと O(N√N) で間に合わない。⇒ 最小値だけほしいので 優先度付きキューで管理できないか検討。区間に含まれたらまず、捨てる予定の集合につっこむ。この集合に存在する要素は、優先度付きキューに含まれていないが、最小値でなので捨てられない要素である。つまり、出力時に、キューの最小値をこの集合で検索し、あれば両方から取り除き、なければその値を最小値として出力すればよい。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3012066/1cb3c19e-828b-1d1b-95e7-965deedb1951.png)


あとは区間から溢れる要素に対する処理である。まず、同じ要素が新しい区間に含まれるならば、キュー、集合 ともに操作を行う必要がないことがわかる。よって、各値ごとに区間に含まれる最も右側の位置を管理したくなる。これは defaultsict で管理するとして、もしあふれる位置と最大値が等しければ捨てる予定集合　または キューを操作する必要がある。捨てる予定集合になければキューからも捨てられてしまっているので、push する。捨てる予定集合にまだあれば、キューからは捨てられていないので、集合から捨てればよい。

⇒　類題: 281E 

➀' 実は　　　追記 230215

実は 削除待ち集合は必要なく、個数が 0 でない要素なら削除する処理で十分である。むしろこちらの方が、重複を許した push が可能になる。これによって削除待ち集合が空なら～みたいなことを考える、実装する必要がなくなりくそ楽。281E でも同様に個数で管理できる。

基本的に削除待ち集合での管理は条件が増えて面倒なので、**個数管理** を優先することにする。


➁ 別解 1

$mex$ : 区間に含まれない & 最小値

⇔ **区間に含まれる要素を ∞ (最小値に影響させない)とした 1 ～ N までの最小値** と解釈することができる。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3012066/84088118-7ae3-6897-b9ec-ac1bfc910889.png)


この時、含む含まないの変更にまつわる1点更新 & $\ [1,N+1)$ 区間取得 が必要な操作となるため、**セグメントツリー** でデータを管理すればクエリごとに $O(logN)$ で十分高速に処理可能

つまり単位元を $∞$ , 更新関数を $min$ として、区間に含まれる要素の位置には単位元を、含まれない要素の位置にはその index 番目を与えて、N-M+1 個の区間それぞれで $mex$ : $min(\ [1,N+1)\ $)  を求めればよい


参考: https://marco-note.net/abc-194-work-log/



③ 別解 2

現在手札にない。思いつかない。

qita 記事そのまま引用

$0 ≦ mex ≦ N+1$ を満たす。もし、mex = 0 であれば、N-M+1 の少なくとも 1つの区間では 0が含まれないことになる。

これを判定することは実は難しくなく、**0 が存在する位置の間隔で判定可能**。もし、M 以上の間隔があれば、その中に必ず 0 が含まれない区間が存在する

逆に、すべての間隔で M 未満であれば、すべての区間で 0 を含むので mex ≒ 0 

よって、次に mex = 1  であるか考える。本来であれば $N-M+1$ の少なくとも 1つの区間では 1 が含まれないこと、に加えすべての区間で 0を含むこと、が条件ですが後者は既に成立。したがって、前者を 1が存在する位置の間隔で判定すれば十分。

これ以降も、同様にして mex が確定するまで判定し続ける。

あらかじめ各数字の位置を求めておけば、計算量は全体で $O($ **間隔の数** $)$ 間隔を簡単に求めるために、どの数字も先頭と末尾に含まれる調整を施しても全体で N+N 個の間隔しかないので、十分高速。

参考 : [公式Youtube 動画](https://www.youtube.com/watch?v=avazOGG7OfY)




④ 補足 defaultdict　初期化

0 で初期化してしまうので、最も右側にある位置を 1-indexed で表現する必要があった。

![image](https://user-images.githubusercontent.com/109026838/218320358-f28be42f-834c-459e-a9d8-02b810a059b9.png)

参考:https://qiita.com/xza/items/72a1b07fcf64d1f4bdb7

このように lambda -10 とすれば 位置を 0-indexed で管理可能になる。





# 231C Counting2   diff 194  2回目

解答遷移 AC

計 06:04

備考

➀ 思考

整数 i以下の個数を管理すれば、各クエリに O(1) で解答できるが、無理。⇒ ソートして二分探索すれば O(NlogNlogN) で求められる。N<10^5 なので 10^8 は超えないからいけると判断

➁　別解

https://atcoder.jp/contests/abc231/editorial/3075

めちゃくちゃ賢い。クエリを都合の良い順番で答えると二分探索を繰り返す必要がない。

類題 235E 0222

# 0215

# 146D Coloring Edges on Tree  diff 1192

解答遷移 AC

計 25:55

備考

➀ 思考

最大次数頂点から伸びる辺の色を決定していけばよい。その次数を K とすると、他の頂点から伸びる辺を決定するために K 以下回数必要だが、これでは O(NK) で間に合わない。⇒ しかし、よく考えるとその頂点の次数回で色を決定することが可能なので、普通の BFS と同じ計算量 O(2M) で間に合うと考えた、、、と思う　(少し記憶曖昧) 

実装では、辺の色 および 頂点の色を管理し、色 i で決定した辺の先の頂点の色 を i とすることで、色の重複を防ぐことにした。

➁ 解法

方針は◎ 。 意識できれば良かった点は、グラフが木であるから色が次数以下で決定すること。木でなければ既に色が決定した頂点へ辺がつながることもあり、その辺の色はその頂点とも重複することができないので、次数を超えうることになる。

また、次数最大の頂点からスタートする必要も実はない。この場合、以下のように i-indexed で辺の番号を与えると都合がいいい

https://zenn.dev/knk_kei/articles/abc-146-d-coloring-edges-on-tree


# 126D  Even Relation  diff 1279

解答遷移　WA AC

計 17:21 +05:00

備考

➀ 思考

共通祖先で距離を表現するのかと思ったが、単に隣接辺の偶奇に注目し偶数なら同じ色、奇数異なる色で両頂点を決定することができると判断。普通に適当な始点から BFS して現在の頂点の色 xor 辺の偶奇 で先の頂点の色を求めた。



# 209D Collision  diff 686 

解答遷移 AC

備考

➀ 思考

d_ab = d_0a + d_0b - 2 × d_co(共通祖先までの距離) で任意の二点間の距離が求まるので、共通祖先を求めたい。⇒ 木は根まで logN 回でさかのぼれることに注目し、prev 配列をもっておけば c,d の経路を復元できるので、この共通部分の長さを求めればよいと判断しそうになったが、ここで d_ab の偶奇にしか興味がないことに気づいて、d_co　を求めずに解答

※ logN でさかのぼれるのは完全二分木の場合だけである。1 ～ N まで一本道の場合 O(N) かかるので無理

➁　別解

木の二分グラフ性に注目すれば、始点からの距離の偶奇が異なる頂点から頂点へは移動できない。したがって、d_0a,d_0b の偶奇を評価するだけでいい。


# ☆ Many Requirements   diff 1136

降参

備考

➀ 思考

 A を全探索できたらうれしいが、無理　⇒ 前から順に決まるのではなく、全ての位置について常に判定する必要があるので、最後尾の情報だけ持つ dp みたいなことができない。⇒ つまり、やはり全列挙したいが、どうすればいいかわからず降参
 
 ➁ 解法
 
 本当に全列挙は間に合いませんか？ 少し複雑な数え上げだからって、どうしてさぼろうとするの？なんでプログラミングできる環境があるのに、手計算しようとするの？
 
 全列挙しなければいけない数は見た目より死ぬほど少ない。再帰で A を作って判定すればいいだけ。最悪


# 253C Max - Min Query   diff 518  2回目

解答遷移 WA WA AC

計 32:46 + 10:00

備考

➀ 思考

281E , 194E 同様、任意の要素の追加,削除,および最小値の出力を高速で行うデータ構造でクエリを処理する問題なので、削除待ち集合 と優先度付きキューの合わせ技で最小値のみを削除することにした。WA を出してしまったが、要素を追加する際は、削除待ちの要素であるかどうかを確認しなければならないことに気を付けて AC

➁ 解法

194E でも追記したが、削除待ち集合でなく、個数で管理する方が実装が簡単になる。どういうことかというと、削除待ち集合での管理は、WA を出したようにヒープに要素を重複して追加することを防ぐた必要があり、これが忘れたり面倒くさい。⇒ 最小値が個数 0 であれば削除し続ける処理であれば、ヒープに同じ値が重複していても関係なく全部削除してくれる。

# ☆ 281E Least Elements  diff 1334

備考

➀ 解法

253C , 194E 281E , 194E 同様、任意の要素の追加,削除,および最小値の出力を高速で行うデータ構造でクエリを処理する問題である。したがって、削除待ち集合 or 個数管理 によって、最小値のみを削除することができれば OK

類題より要求される処理が多く少し面倒だが、本質は全く同じ


# 0216

# トポロジカルソート勉強

![image](https://user-images.githubusercontent.com/109026838/219209707-5467dfa8-7826-4699-a6e7-f2531363eb89.png)

入次数 0 の頂点から順に探索し、次に入次数 0 のものを探していき順番を求めるアルゴリズム。

実装では、乳児数を管理するテーブルを用いて、入次数 0 の頂点から bfs で探索する。

# ☆ 223D Restricted Permutation  diff 1069

降参

備考 

➀　思考

有向サイクルがあれば成立不可なことはわかったが、どうやって順番を求めればよいかが全く分からず降参

➁　解法

トポロジカルソートした順番を求める。辞書順にするために、キューで持たず優先度付きキューで BFS する。また、１つでも有向サイクルを持つ連結成分があるかを order サイズで検出する。


# 0217 

# 234E Arithmetic Number  diff 899

解答遷移 (RE+WA) WA AC

計 52:49 + 10:00

備考

➀ 思考

初項 と 第2項 の差に注目し、この差で L桁の数が作れた場合にそれが X 以上であれば条件を満たす。そうでなければ公差を +1 して再び判定。これを繰りかえし 公差が 9 になっても条件を満たさない場合、初項を +1 して判定すればよい。これで必ず条件を満たす数を求められる。ただし、初項 9 の場合には 1 続く L+1 桁の数になることに注意

➁ 別解

10 ～ 99 までの数に対して条件を満たす L 以下の数を dfs や bfs で生成するのも可能。u2dayo が参考になる。

③ 反省

遅い。公差と数列はセット + 交差: -9 ～ 9 だから 余裕で数列を生成できることに気づくまでにかかる時間がおそすぎる。

まあ、自分ができる前提だから怒りを覚えているが、そもそも全列挙計算量推定が苦手なので、最終的に気付けただけでもいいかもしれない。


# 097D  Equals  diff 1270

解答遷移 AC

計 28:03

備考

➀　思考

転倒数がまず気になったが、順列を戻すのでなく特定の列に一致させる問題でないので関係なさそう。⇒ 既に一致している場所の扱いが気になったので考察すると、1 3 2 (1,2) (1,3) の例で、一度一致数を減らした方が良い場合を発見。これで各操作を前から考えるような問題ではないと判断 ⇒ この例から、pi が移動可能な領域は i と交換可能な x,y 全域になることがわかった。グラフ的に考えると、同じ連結成分である領域に移動可能ということなので、Uion-Find で考えるのが良さそう ⇒ あとは、値 x の初期 index と x が同じ連結成分であれば px = x  となるので、uf.same でこれを判定して AC

➁ 感想

完璧。必要な情報は何で、そのために何を求めるか、綺麗に道を切り開けた。

# 166E This Message Will Self-Destruct in 5s  diff 1062

解答遷移 RE AC

計 18:21 + 10:00

備考

➀　思考

全ペア探索は当然無理なので、数式理解を試みる ⇒ Ai + Aj = |j-i| ここで、i < j の順に探索すれば、j - Aj = (Ai+i) が成立する。したがって、i の探索時にあらかじめ j-Aj を満たす j の個数を求めればよいと判断。 A が大きすぎるので、テーブルの範囲外を参照しないように気を付けて AC

# 188E  Peddler  diff 1170

解答遷移 (TLE+WA) AC

計 1:08:48 + 05:00

➀ 思考

町 i での売買では 町 i 以前で買える最小金額との差分が最大値となる。よって、経路最小金額を保存しておく必要がある。あとはダイクストラで各町を、その町にたどりつくまでの金額順に確定させていけばよいと判断。計算量はO(MlogM)で十分高速

➀' WA　＋TLE 

最小金額テーブルを作成せずに、A を更新していけばよいと考えたが、これでは複数の 町 i への流入経路をすべて採用してしまい計算量が爆発するおそれがある。具体的にはある経路の最小値 Ai' で Ai を更新してしまうと、他のすべての経路も 町 i　までの最小値 が Ai' となるからである。

そもそも、他の経路での売買価格がずれてしまうので A を直接更新せず、最小値テーブルをきちんと持つ必要がある(WAの原因)。


➁ 解法

dp[i] : i　までの最小金額とすれば、A[i] - dp[i] で差額をもとめられる。遷移は dp[i] = min(dp[i],dp[j],A[i]) ※ 公式解説は添え字が間違っている。


# 0218

# ☆ 240E  Ranges on Tree  diff 1068

降参

➀　思考

x個の葉を、(1,1) , (2,2) ... (x,x) と命名し、根まで親の(最小値,最大値) 更新すればよいと分かった。したがって、各頂点の最大値テーブルと、最小値テーブルを作成し、葉を特定した後トポロジカルソートの要領で親のテーブルを確定させていけばよいと判断した。⇒ WA (1:00:00) ⇒ これでなぜだめか全くわからず降参 

➁ 解法

ほとんど正解なのだが、葉の命名を適切に行えなかったのが WA の原因

![image](https://user-images.githubusercontent.com/109026838/219787608-4d7074c2-1a90-4f7a-95a0-85c270272593.png)

葉の特定で行ったように、dfs 帰りがけで命名していけばよい。

なお、葉の名前はグローバル変数で管理した。帰りがけにインクリメントして、引数でも持ち越せば一応グローバル変数に頼らない命名ができるが、ややこしいのでおとなしくグローバル変数化するのが良いと思う。


# 179E Sequence Sum  diff 1175

解答遷移 RE RE AC

計 1:17:16+10:00

➀ 思考

鳩ノ巣理論で M 回で必ずループが見つかることを理解。 ⇒ 余りの重複でループを検知し、またそれ至る回数が知りたいので、dp1[i] : 余り i となる回数 を管理 ⇒ さらに、 x回目 ～ y 回目 でループするならば、1回目 ～ x-1 回目までの和 , x ～ y 回目までの和が知りたい。つまり、dp2[j] : j 回目 での総和 も管理する必要がある。なお、各余りはは dp2[j] - dp2[j-1] で求められるので別で管理する必要はない

この場合、rep: (N-y) // (y - (x-1)) 回 x ～ y 回目 をループする。※ x≦y より分母>0 したがって、求める和は dp2[y] + (dp2[y]-dp2[x-1]) * rep + dp2[ ( N-y ) % ( y- (x-1) ) + x-1 ] - dp2[x-1] となる。



➀' 注意点

まず、 dp2[j] : j 回目を **含んだ** 総和であるので、 ループ回数は y - (x-1) , 和は dp2[y]-dp2[x-1] となる。

また、M 回目 で初めてループを検知する場合、dp1 のサイズは M+1 以上が要求される ( 回数を 1-indexed で定義しているため)

鳩ノ巣理解 + 必要情報精査までは完璧だったが、これら index 関連でごちゃごちゃになってくそおそくなった

# 0221

# ☆ ループ構造検出問題

・ループ検出のために、操作回数 ⇔ 余り で両引きする必要がある。

・index が絡むのでこんがらがるが、以下のポイントで定義することで楽できる

![image](https://user-images.githubusercontent.com/109026838/220275556-c6c6d7b5-310a-4442-a0cc-61356da26bef.png)

このように、重複を初めて検出する位置を終点、既出位置を始点とすることで、ループ構造の長さを 終点 - 始点 で求められる。これは非ゼロであり、初期値自己ループにも対応できるので最強

また、1-indexed で定義しているため、テーブルサイズは N+1 以上必用

# 0222

# 248D Range Count Query  diff  793

解答遷移 AC

計 15:42

➀ 思考

値ごとに出現位置を調べて二分探索して個数を求める。

価ごとにセグ木を管理して区間の個数を調べるにはメモリが N^2 必要なので無理と判断した。(初期化するのも O(N^2) で無理)

# 235E MST +1  diff 1304

解答遷移 AC

計 13:43

➀ 思考

クラスカル法で最小全域木を構築したい。⇒ クエリの辺も一緒に見ていき、クエリの辺が最小全域木をなすなら、それを記憶する処理を実行すればよいと判断。具体的には table[i] : i番目のクエリの辺が最小全域木をなす を作成し、N+Q の辺を順番付きで重み順にソートする。エリの辺ならばテーブルを更新、そうでなければグラフを構築する。


➁ 類題

231C 


# 226E Just one   diff 1327

解答遷移 WA AC

計 50:17

➀ 思考

連結成分ごとに計上し、各連結成分にちょうど１つサイクルがあれば組み合わえは2倍になることがわかった。⇒ 連結成分ごとに DFS で探索し、union-find でサイクルを検知する。一度探索した頂点を seen で管理することで全体で O(2M) となり十分高速

![image](https://user-images.githubusercontent.com/109026838/220481010-d57f33b6-beef-473d-b3b7-1a6f8b87f5cd.png)


➁ 解法

サイクルが1つのみ存在する場合 頂点数 × 2 = 辺数 が成立するので　dfs で辺と頂点をカウントすればよい

③ 疑問

なぜか uf + dfs のコードは pypy3 で提出しても AC できたが、ここから uf を削除しただけのコードは pypy3 では TLE した。

どちらも python でしか通らないなら理解できるが、どうして片方のみ pypy でも通ったのか意味不明


































