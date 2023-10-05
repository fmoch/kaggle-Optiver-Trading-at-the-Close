# kaggle Optiver - Trading at the Close

Optiver - Trading at the Closeコンペのリポジトリ

- result
  - public: ●●
    - rank: ●●/●●
  - private: ●●
    - rank: ●●/●●

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

### Submit

提出物は、予測リターンと観測されたターゲットとの間の平均絶対誤差（MAE）で評価される。計算式は次式で与えられる：

$$ 𝑀𝐴𝐸=1/𝑛∑𝑖=1𝑛𝑦𝑖-𝑥𝑖| 𝑀𝑥𝑦 $$

ここで
n はデータ点の総数。
y_i はデータ点 i の予測値。
x_i はデータ点 i の観測値。
応募
このコンペティションには、提供されている python の時系列 API を使って提出しなければなりません。APIを使用するには、このノートブックのテンプレートに従ってください。.5,0.5

## Timeline

- 2023年5月11日 - 開始日
- 2023年8月3日 -エントリー締切。出場するには、この日までに競技規則に同意する必要があります。
- 2023年8月3日 - チーム合併の締切日。この日が、参加者がチームに参加したり合併したりできる最後の日です
- 2023年8月10日 - 最終提出締切日。

## Data

競技データは、3つの年齢関連疾患に関連する50以上の匿名化された健康特性で構成されています。目標は、被験者がこれらの疾患のいずれかに罹っているかいないかを予測することである（二値分類問題）。

なお、これはコードコンペティションであり、実際のテストセットは隠されている。このバージョンでは、解答を作成するのに役立つように、正しい形式のサンプルデータをいくつか提供します。あなたの提出物が採点されるとき、このサンプルテストデータはフルテストセットに置き換えられます。完全なテストセットには、約400行があります。

- **train.csv** - The training set.
- **test.csv** - The test set.
- **greeks.csv** - 補足的なメタデータ。トレーニングセットでのみ利用可能。
- **sample_submission.csv**

### train.csv

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
