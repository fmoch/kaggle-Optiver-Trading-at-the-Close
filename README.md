# kaggle Optiver - Trading at the Close

Optiver - Trading at the Closeコンペのリポジトリ

- result
  - public: ●●
    - rank: ●●/●●
  - private: ●●
    - rank: ●●/●●

***

## Overview

### 競技の目的

このコンペティションでは、注文帳簿と終値オークションのデータを使用して、ナスダック上場銘柄の終値の動きを予測できるモデルを開発することに挑戦します。　　
オークションからの情報は、価格の調整、需給ダイナミクスの評価、取引機会の特定に使用できます。

### コンテキスト

　証券取引所は、一刻を争うハイペースな環境である。一日の取引が終わりに近づくにつれ、その激しさはエスカレートし、最後の10分間がピークとなる。ボラティリティの高まりと急激な価格変動が特徴的なこの瞬間は、その日の世界経済のシナリオを形成する上で極めて重要な役割を果たします。　　ナスダック証券取引所の各取引日は、ナスダックのクロージングクロスオークションで終了します。このプロセスによって、取引所に上場している証券の公式な終値が決定されます。これらの終値は、投資家、アナリスト、その他の市場参加者にとって、個々の証券や市場全体のパフォーマンスを評価する上で重要な指標となります。　　
　この複雑な金融情勢の中で、世界をリードする電子マーケット・メーカーであるオプティバーは活動しています。技術革新を原動力として、オプティバーは、デリバティブ、現物株式、ETF、債券、外貨などの膨大な金融商品を取引し、世界の主要取引所において、何千ものこれらの商品に競争力のある両建て価格を提供しています。　　
　ナスダック取引所の取引セッションの最後の10分間に、オプティバーのようなマーケットメーカーは従来のオーダーブックデータとオークションブックデータを統合します。両ソースからの情報を統合するこの能力は、すべての市場参加者に最良の価格を提供するために不可欠です。　　
　このコンペティションでは、オーダーブックとオークションの終値データを使用して、ナスダック上場銘柄の終値の動きを予測できるモデルを開発することが求められます。オークションからの情報は、価格の調整、需給ダイナミクスの評価、取引機会の特定に利用できます。　　
　あなたのモデルは、オークションとオーダーブックからのシグナルの統合に貢献し、特に取引の最後の10分間の激しい動きにおいて、市場の効率とアクセスの改善につながります。また、オプティバーのトレーダー、クオンツ・リサーチャー、エンジニアが直面するような、現実世界のデータサイエンスの問題を扱う実体験も得られます。　　

***

### Submit

提出物は、予測リターンと観測されたターゲットとの間の平均絶対誤差（MAE）で評価される。計算式は次式で与えられる：

$$ 𝑀𝐴𝐸=\displaystyle\frac{1}{𝑛}\displaystyle\sum^{n}_{i=1}|𝑦_𝑖-𝑥_𝑖| $$

ここで
$ n $ はデータ点の総数。
$ y_i $ はデータ点 $ i $ の予測値。
$ x_i $ はデータ点 $ i $ の観測値。

#### 応募

このコンペティションには、提供されている python の時系列 API を使って提出しなければなりません。APIを使用するには、このノートブックのテンプレートに従ってください。.5,0.5

#### コード要求

このコンペティションへの投稿は、ノートブックを通じて行う必要があります。コミット後に「Submit」ボタンが有効になるためには、以下の条件を満たす必要があります  

- CPUノートブック <= 9時間のランタイム
- GPUノートブック <= 9時間ランタイム
- インターネットアクセスが無効
- 訓練済みモデルを含め、自由に一般利用可能な外部データを許可する。
- 提出ファイルはsubmission.csvという名前で、APIによって生成されたものでなければなりません。
投稿方法の詳細については、コードコンペティションFAQを参照してください。また、投稿エラーが発生した場合は、コードデバッグのドキュメントを確認してください。

***

## Timeline

- 2023年9月20日  -  開始日
- 2023年12月13日 - エントリー締め切り。
- 2023年12月13日 - チームマージ切日。
- 2023年12月20日 - 最終提出期限。

すべての締め切りは、特に断りのない限り、該当日の午後11時59分（UTC）です。大会主催者は、必要と判断した場合、コンテストのタイムラインを更新する権利を有する。

予想タイムライン：
最終提出期限以降、選択されたノートブックに対して実行される市場データの更新を反映するため、リーダーボードが定期的に更新される。更新はおよそ2週間ごとに行われる。

- 2024年3月20日 - コンペティション終了日

***

## Data

 このデータセットには、NASDAQ 証券取引所の毎日 10 分間の終値オークションのヒストリカルデータが含まれている。あなたの課題は、ナスダック上場銘柄で構成される合成指数の将来の値動きに対する、銘柄の将来の値動きを予測することです。

 これは時系列APIを使った予測競技です。非公開のリーダーボードは、提出期間終了後に収集された実際の市場データを使用して決定されます。

- **train.csv** - The training set.
- **test.csv** - The test set.
- **greeks.csv** - 補足的なメタデータ。トレーニングセットでのみ利用可能。
- **sample_submission.csv**

### train/test .csv

|カラム名|説明|
|----|---- |
|stock_id | 銘柄の一意な識別子。すべての銘柄 ID がすべてのタイムバケットに存在するとは限らない。|
|date_id | 日付を表す一意の識別子。日付 ID は連続したもので、全銘柄で一貫している。|
|imbalance_size | 現在の基準価格における未マッチ額 (単位は USD)。|
|imbalance_buy_sell_flag | オークションの不均衡の方向を反映する指標。|
||バイサイドインバランス; 1|
||セルサイドインバランス; -1|
||インバランスなし;0|
|reference_price | ペア株が最大になり、インバランスが最小になり、ビッド・アスクの中間点からの距離が最小になる価格。ビッドとアスクの中点からの距離が最小となる価格。|
|matched_size | 現在の基準価格でマッチング可能な金額（単位はUSD）。
|far_price | オークションの関心のみに基づき、マッチング株数を最大化する交差価格。この計算では連続成行注文は除外されます。|
|near_price | オークション注文と連続成行注文に基づく約定株数を最大化するクロッシン グ価格。|
|[bid/ask]_price | ノンオークションブックで最も競争力のある買い/売りレベルの価格。|
|[bid/ask]_size | ノンオークションブックで最も競争力のある買い/売りレベルの想定元本金額。|
|wap | ノン・オークション・ブックにおける加重平均価格。  $\displaystyle\frac{𝐵𝑖𝑑𝑃𝑟𝑖𝑐𝑒∗𝐴𝑠𝑘𝑆𝑖𝑧𝑒+𝐴𝑠𝑘𝑃𝑟𝑖𝑐𝑒∗𝐵𝑖𝑑𝑆𝑖𝑧𝑒}{𝐵𝑖𝑑𝑆𝑖ze+𝐴𝑠𝑘𝑆𝑖𝑧𝑒}$|
|seconds_in_bucket | その日の終値オークションの開始からの経過秒数。|
|target | 銘柄のワップにおける 60 秒後の将来の値動きから、合成指数の 60 秒後の将来の値動きを差し引いた値。列車セットに対してのみ提供される。合成インデックスは、Optiver がこのコンペティションのために構築したナスダック上場銘柄のカスタム加重インデックスである。ターゲットの単位はベーシス・ポイントで、これは金融市場で一般的な測定単位である。1ベーシスポイントの値動きは0.01%の値動きに相当する。tは現在の観測時間であり、ターゲットを定義することができる：𝑇𝑎𝑟𝑔𝑒𝑡=(𝑆𝑡𝑜𝑐𝑘𝑊𝐴𝑃𝑡+60𝑆𝑡𝑜𝑐𝑘𝑊𝐴𝑃𝑡−𝐼𝑛𝑑𝑒𝑥𝑊𝐴𝑃𝑡+60𝐼𝑛𝑑𝑒𝑥𝑊𝐴𝑃𝑡)∗10000|

|カラム名|説明|
|----|---- |
|id| 各オブザベーションの一意な識別子|
|AB-GL|56個の匿名化された健康特性。EJはカテゴリーであるが、それ以外はすべて数値である。|
|class|バイナリターゲット：1は、被験者が3つの条件のうちの1つと診断されたことを示し、0は、診断されていないことを示す|

### greek.csv

|カラム名|説明|
|----|---- |
|Alpha|年齢に関連する状態がある場合、その種類を特定する。|
|A|年齢に関連した状態はない。クラス0に対応する。|
|B, D, G|3つの加齢に関連した状態。クラス 1 に対応する。|
|Beta, Gamma, Delta|3つの実験特性を示す。|
|Epsilon|この被験者のデータが収集された日付。なお、テストセットのデータはすべてトレーニングセットが収集された後に収集されたものである。|

## 参考

|notebook|説明|
|---|---|
|[ICR IARC EDA Ensemble and Stacking baseline](https://www.kaggle.com/code/tetsutani/icr-iarc-eda-ensemble-and-stacking-baseline)|ベースライン（仮）|
|[ICR - EDA & Balanced Learning with LGBM & XGB](https://www.kaggle.com/code/mateuszk013/icr-eda-balanced-learning-with-lgbm-xgb)|EDA参考|
|[icr-identify-age](https://www.kaggle.com/code/vadimkamaev/icr-identify-age)|Tabpfnを用いたノート, LB上位 (0.11)はこのTabPFN使用している|

## NOTE

### nb

|notebook|CV|PV|説明|
|---|---|---|---|
|kg-nb_ICR_001|0.13968 ± 0.08848|0.28|[ICR IARC EDA_Ensemble and Stacking baseline](https://www.kaggle.com/code/tetsutani/icr-iarc-eda-ensemble-and-stacking-baseline) をコピーして作成|
|kg-nb_ICR_002|56.3||001ベース、中身の説明追加|

### EXP

|notebook|CV|PV|説明|
|---|---|---|---|
|kg-nb_ICR_exp_001||0.23|kg-nb_ICR_001をベースに、EDA用のノートブック作成|
|kg-nb_ICR_exp_002|-|-|飛び番号|
|kg-nb_ICR_exp_003|0.18385 ± 0.06902|0.40|001ベース、drop column変更, EDA削除|
|kg-nb_ICR_exp_004|||[icr-identify-age](https://www.kaggle.com/code/vadimkamaev/icr-identify-age) をコピーして作成, |
|kg-nb_ICR_exp_005_ver1|||003ベース, `drop_cols` =['BC', 'CL','BZ','DV']|
|kg-nb_ICR_exp_005_ver2||| `drop_cols` =['BC', 'CL','BZ','DV','AR]|
|kg-nb_ICR_exp_005_ver3|||ver2の設定のままearly_stopping_rounds = 1000 -> 10000,Early_stoppingに伴うオーバーフットを検証
|
early_stopping_rounds = 100000|

## LOG

1920
