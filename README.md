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


③ 別解

DP　でも解答可能。遷移が同じ行で一度きりであることから dp テーブルを使いまわせるので 一次元で十分。

遷移を ➁ の方向とは逆に考えることに注意

④ 注意点

・まずメモ化再帰における引数 maxsize は記憶可能数であり、再帰上限ではない。つまり、普通の再帰処理同様、setcursionlimit で上限を設定しなす必要がある。

・こちらも当然ではあるが、再帰なので pypy < python である。




































