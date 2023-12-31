# kaggle Optiver - Trading at the Close

![BOY](https://github.com/fmoch/kaggle-Optiver-Trading-at-the-Close/assets/116940479/abacdaa9-b706-4caa-b73d-408465b7d6b8)

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

## Timeline

- 2023年9月20日  -  開始日
- 2023年12月13日 - エントリー締め切り。
- 2023年12月13日 - チームマージ切日。
- 2023年12月20日 - 最終提出期限。

すべての締め切りは、特に断りのない限り、該当日の午後11時59分（UTC）です。大会主催者は、必要と判断した場合、コンテストのタイムラインを更新する権利を有する。

予想タイムライン：
最終提出期限以降、選択されたノートブックに対して実行される市場データの更新を反映するため、リーダーボードが定期的に更新される。更新はおよそ2週間ごとに行われる。

- 2024年3月20日 - コンペティション終了日

## Data

 このデータセットには、NASDAQ 証券取引所の毎日 10 分間の終値オークションのヒストリカルデータが含まれている。あなたの課題は、ナスダック上場銘柄で構成される合成指数の将来の値動きに対する、銘柄の将来の値動きを予測することです。

 これは時系列APIを使った予測競技です。非公開のリーダーボードは、提出期間終了後に収集された実際の市場データを使用して決定されます。

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
|wap | ノン・オークション・ブックにおける加重平均価格。  $\displaystyle\frac{Bidprice∗AskSize+AskPrice∗BidSize}{BidSize+AskSize}$|
|seconds_in_bucket | その日の終値オークションの開始からの経過秒数。|
|target | 銘柄のワップにおける 60 秒後の将来の値動きから、合成指数の 60 秒後の将来の値動きを差し引いた値。列車セットに対してのみ提供される。|
||合成インデックスは、Optiverがこのコンペティションのために構築したナスダック上場銘柄のカスタム加重インデックスである。|
||ターゲットの単位はベーシス・ポイントで、これは金融市場で一般的な測定単位である。|
||1ベーシスポイントの値動きは0.01%の値動きに相当する。tは現在の観測時間であり、ターゲットを定義することができる|
||$Target = (\displaystyle\frac{StockWAP_{t+60}}{StockWAP_t}−\displaystyle\frac{IndexWAP_{t+60}}{IndexWAP_t})∗10000$|

サイズに関する欄はすべて米ドルベースである。
価格関連の列はすべて、オークション期間開始時の株価 wap (加重平均価格)に対する値動きに変換される。

- **sample_submission**
  - APIによって配信される有効なサンプルサブミッション。サンプルサブミッションの使用方法の非常に簡単な例については、このノートブックを参照してください。

- **revealed_targets**
  - 各日付の最初のtime_idの時(つまりseconds_in_bucketがゼロの時)、APIは前の日付全体の真のターゲット値を提供するデータフレームを提供します。それ以外の行には、対象となるカラムの null 値が含まれます。

- **public_timeseries_testing_util.py**
  - カスタムオフラインAPIテストを簡単に実行するためのオプションファイルです。詳細はスクリプトのdocstringを参照してください。使用する前にこのファイルを編集する必要があります。

- **example_test_files/**
  - API の機能を説明するためのデータです。APIが提供するのと同じファイルとカラムを含む。最初の3つの日付IDは、APIがどのように機能するかを説明できるように、訓練セットの最後の3つの日付IDの繰り返しである。

- **optiver2023/**
  - APIを有効にするファイル。APIが5分以内にすべての行を配信し、0.5GB未満のメモリを確保することを期待する。APIによって配信される最初の3つの日付IDは、APIがどのように機能するかをよりよく説明するために、訓練セットの最後の3つの日付IDの繰り返しである。APIを進めるためには、これらの日付について予測を行う必要があるが、これらの予測はスコア化されない。

## 参考

|notebook|説明|
|---|---|
|[Summarizing our collective learnings over the past month](https://www.kaggle.com/competitions/optiver-trading-at-the-close/discussion/448920)|コンペ開始から１ヶ月時点での有用な情報をまとめている、基本的にはここをベースに描く情報をそれぞれ参照する|
|[[Optiver] Simple LGBM for beginner (Eng/日本語)](https://www.kaggle.com/code/junjitakeshima/optiver-simple-lgbm-for-beginner-eng)|すでに日本語訳のノートブック。シンプルなLGBMモデルの説明|
|||

## NOTE

### nb

|notebook|CV|PV|説明|
|---|---|---|---|
|kg-nb_optiver_001|||[[Optiver] Simple LGBM for beginner (Eng/日本語)](https://www.kaggle.com/code/junjitakeshima/optiver-simple-lgbm-for-beginner-eng)をコピーして作成|

### EXP

|notebook|CV|PV|説明|
|---|---|---|---|
|kg-nb_ICR_exp_001||0.23|kg-nb_ICR_001をベースに、EDA用のノートブック作成|

## LOG

### 20231008

- リポジトリ作成

### 20231011

- git関連一旦まとめ

### 20231014

- 以下ノートをまずは眺める

  - [[Optiver] Simple LGBM for beginner (Eng/日本語)](https://www.kaggle.com/code/junjitakeshima/optiver-simple-lgbm-for-beginner-eng)

### 20231015

- kg-nb_optiver_001
  - 上記ノートブックの写経で内容把握  
stock_id                       200
date_id                        481  
seconds_in_bucket               55  
imbalance_size             2971863  
imbalance_buy_sell_flag          3  
reference_price              28741  
matched_size               2948862  
far_price                    95739  
near_price                   84625  
bid_price                    28313  
bid_size                   2591773  
ask_price                    28266  
ask_size                   2623254  
wap                          31506  
target                       15934  
time_id                      26455  
row_id                     5237980  
dtype: int64

### 20231018

- train 相関ヒートマップで確認
![heatmap](https://github.com/fmoch/kaggle-Optiver-Trading-at-the-Close/assets/116940479/a9ccebb3-2669-4c9f-9c19-c5b390ba6678)

- 以下のカラムはそれぞれ相関が高い
  - reference_price：ペア株が最大になり、インバランスが最小になり、ビッド・アスクの中間点からの距離が最小になる価格。ビッドとアスクの中点からの距離が最小となる価格。
  - bid_price：ノンオークションブックで最も競争力のある買いレベルの価格。
  - ask_price：ノンオークションブックで最も競争力のある売りレベルの価格。
  - wap：ノン・オークション・ブックにおける加重平均価格。 
- reference_priceはbidとaskそれぞれから求まるため、必然的に相関高くなっている
- wapは次の式のため $\displaystyle\frac{Bidprice∗AskSize+AskPrice∗BidSize}{BidSize+AskSize}$
  - 一方でAsk_size, Bid_sizeは相関係数0.2程度と小さい
- 以下もついで相関がお互いある
  - near_price オークション注文と連続成行注文に基づく約定株数を最大化するクロッシング価格。
  - imbalance_buy_sell_flag	オークションの不均衡の方向を反映する指標

### 20231022

- [Summarizing our collective learnings over the past month](https://www.kaggle.com/competitions/optiver-trading-at-the-close/discussion/448920)　を参照に主要な投稿を確認する。

### 20231024

以下訳。

- 投票上位5カーネル

> - <https://www.kaggle.com/code/tomforbes/optiver-trading-at-the-close-introduction>
>   - これは投稿を構築するために使用され、APIの効果的な使用を示しています。
> - <https://www.kaggle.com/code/ravi20076/optiver-baseline-models>
>   - コミュニティに心から感謝する。
> - <https://www.kaggle.com/code/yuanzhezhou/baseline-lgb-xgb-and-catboost>
>   - この課題のためのシンプルなMLモデルの使い方を説明するもので、便利な二次機能もたくさんある。
> - <https://www.kaggle.com/code/a27182818/explain-the-data-lightgbm-baseline>
>   - これはシンプルなLight GBMカーネルで、コードは初心者にやさしい。
> - <https://www.kaggle.com/code/iqbalsyahakbar/optiver-a-starter-s-notebook>
>   - 非常に初心者に優しいスターターカーネルで、関連する説明があります。

- トップ5パブリック・スコア・カーネル

> - <https://www.kaggle.com/code/siddhvr/optiver-baseline-sub>
> - <https://www.kaggle.com/code/verracodeguacas/hoarders-ensemble>
> - <https://www.kaggle.com/code/miteshadake/lgb-baseline>
> - <https://www.kaggle.com/code/masterray/lgb-baseline>
> - <https://www.kaggle.com/code/leehomhuang/lgb-baseline-train>

- 有用なディスカッションポスト

> - <https://www.kaggle.com/competitions/optiver-trading-at-the-close/discussion/448714>
>   - 投稿のタイミングを知ることができる最近の投稿
> - <https://www.kaggle.com/competitions/optiver-trading-at-the-close/discussion/448069>
>   - 時系列分割CV戦略の使い方を説明した非常に有用な投稿。
> - <https://www.kaggle.com/competitions/optiver-trading-at-the-close/discussion/442851>
>   - 訓練データを使ってインデックスをリバースエンジニアリングしてみる。
> - <https://www.kaggle.com/competitions/optiver-trading-at-the-close/discussion/442453>
>   - Kaggleのトレーディング・コンペティションについて説明している。
> - <https://www.kaggle.com/competitions/optiver-trading-at-the-close/discussion/442632>
>   - サブミッションAPIを使ったローリングフィーチャーの使い方について議論している。

### 20231025
