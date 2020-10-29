# Data Pipeline Casual Talk

データパイプラインに関する議論をカジュアルに行なう会。2019年に4回開催された。  
→ [Data Pipeline Casual Talk - connpass](https://dpct.connpass.com/)

- [Vol.1 [2019.02.13]](#vol1-20190213)
  - [AI・機械学習チームにおけるデータパイプライン構築](#ai機械学習チームにおけるデータパイプライン構築)
  - [データ基盤の3分類と進化的データモデリング](#データ基盤の3分類と進化的データモデリング)
  - [丘サーファーへ「水」を届けるために-これまでとこれから…](#丘サーファーへ水を届けるために-これまでとこれから)
  - [リブセンスのデータ分析基盤とAirflow](#リブセンスのデータ分析基盤とairflow)
  - [データ分析基盤を「育てる」ための技術](#データ分析基盤を育てるための技術)

## Vol.1 [2019.02.13]

[Data Pipeline Casual Talk Vol.1 - connpass](https://dpct.connpass.com/event/114040/)

### AI・機械学習チームにおけるデータパイプライン構築

[AI・機械学習チームにおけるデータパイプライン構築 - Speaker Deck](https://speakerdeck.com/nishiba/aiji-jie-xue-xi-timuniokerudetapaipuraingou-zhu)

- [m3dev/gokart: A wrapper of the data pipeline library "luigi"](https://github.com/m3dev/gokart)
  - > A wrapper of the data pipeline library "luigi".
  - Taskの実装が簡単になる
  - Slackへの通知

### データ基盤の3分類と進化的データモデリング

[データ基盤の3分類と進化的データモデリング #DPCT / 20190213 - Speaker Deck](https://speakerdeck.com/yuzutas0/20190213)

- データ基盤
  - データレイク
    - 元のデータを加工せず、そのまま1つのシステムに集約したもの
    - ただのコピーであることが重要
    - S3やGCSなどのストレージサービスを使うことが多い
  - データウェアハウス
    - 複数のデータを統合&蓄積して、意思決定に使えるように整理したもの
    - 業務ドメイン知識をデータモデリングに反映することが重要
    - Hadoop(hdfs)やRedshift、BigQueryなどの分散データストアを使うことが多い
  - データマート
    - 特定の利用者&用途向けにデータを加工&整理したもの
    - ユースケースごとに最適化されていることが重要
    - Re:dashやTableauなどのBIツールを使うことが多い
- 進化的データモデリングの実践
  - データ基盤の3種別の「技術要素を寄せて」マネジメントする
    - リファクタリングしやすい
    - e.g. BigQuery + SQL + Composer に統一する
  - SQL on パイプライン
    - 加工処理は全てSQLファイルに寄せる + ワークフローエンジンで依存管理

### 丘サーファーへ「水」を届けるために-これまでとこれから…

[DPCT発表資料.pdf - Speaker Deck](https://speakerdeck.com/yuukimiya/dpctfa-biao-zi-liao)

- データにアクセスできない状況からの改善
  - → データパイプラインの整備
    - BigQueryへの連携
    - Tableau Onlineへ定期更新
    - KPIレポートはSlack
- AWSとGCPの役割明確化&担当分担化
  - AWS: セキュアなデータ連携の入り口
  - GCP: データ分析基盤
    - ワークフロー
      - Cloud Composer (Airflow)

### リブセンスのデータ分析基盤とAirflow

[リブセンスのデータ分析基盤とAirflow - Speaker Deck](https://speakerdeck.com/livesense/ribusensufalsedetafen-xi-ji-pan-toairflow?slide=28)

- データ分析基盤
  - Livesense Analytics: データ分析基盤
  - Livesense Brain: 機械学習基盤
- Airflowの活用
  - Redshiftに対する定期的なクエリ実行
  - EMRの起動トリガ
  - Glue起動トリガ
- テスト
- モニタリング

### データ分析基盤を「育てる」ための技術

[building-evolutionary-data-warehouse - Speaker Deck](https://speakerdeck.com/tanakarian/building-evolutionary-data-warehouse)

- データ基盤
  - 「基盤」= 「データの抽出/加工/整形」+「データの可視化、共有」
  - 抽出/加工/整形 → データパイプライン
  - データの可視化、共有 → 各種BIツール
- 育てる
  - アジャイル形式でプロダクトオーナーらと連携し、DWHを洗練させる
- 育てるための技術
  - PoC段階の素早い検証を可能にするBigQueryのView機能、Jupyter
  - 腐敗防止そうで、パイプラインの拡張や変更を強くする
  - パイプラインの各フェーズでの要件/レベルを定め、テストする
    - バルクオーダー: Embulk with Digdag
    - ログ転送: fluentd
    - 分散メッセージング: Cloud Pub／Sub
    - ETL: Cloud Dataflow
    - ワークフロー管理: Cloud Composer
    - データストア: BigQuery, Cloud Storage
