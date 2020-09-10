# Dic Deeper into Data Pipeline

- [About Data Pipeline](#about-data-pipeline)
- [データ基盤](#データ基盤)
  - [データ基盤の種類](#データ基盤の種類)
  - [データ基盤の用途](#データ基盤の用途)
- [データパイプラインとワークフロー管理](#データパイプラインとワークフロー管理)
  - [ワークフロー管理の役割](#ワークフロー管理の役割)
  - [ワークフロー管理ツール](#ワークフロー管理ツール)
  - [パイプラインの記述スタイル](#パイプラインの記述スタイル)
- [References](#references)

## About Data Pipeline

データパイプラインとは、  
**データ基盤へのデータの出し入れや目的に応じたデータ利用を効率よく行うためのデータ処理に関する一連の流れ**

> ![data pipeline image](https://www.hitachi.co.jp/products/it/bigdata/platform/pentaho/article/data-pipeline/images/data-pipeline_img.gif)
> *出典: [3.データ分析を成功へと導くデータパイプライン：Pentaho：日立](https://www.hitachi.co.jp/products/it/bigdata/platform/pentaho/article/data-pipeline/data-pipeline.html#dsp_img) より*

## データ基盤

分析などに利用するデータを蓄積し、必要に応じて取り出すことができる処理システム群

### データ基盤の種類

- データレイク
  - 形式に関わらずデータを集約して保存するストレージリポジトリ
  - 構造化・非構造化の両方のデータを取り扱う
- データウェアハウス
  - 構造化データを収集し、それを目的に応じて定義された形に統合して格納したデータベース
  - 構造化データのみ取り扱う
- データマート
  - 用途に応じて必要なデータだけを抽出・加工してまとめたデータベース

### データ基盤の用途

- レポーティング分析
- アドホック分析
- 機械学習・AI
- モニタリング・監視

## データパイプラインとワークフロー管理

データパイプラインの実現 → ワークフロー管理

### ワークフロー管理の役割

- タスクのスケジューリング
- タスクの並列実行
- タスクの依存関係の解決
- エラーからのリカバリ能力

### ワークフロー管理ツール

- [Apache Airflow](https://airflow.readthedocs.io/en/latest/)
  - Airbnb開発
  - Python製
  - DAG型
- [Luigi](https://luigi.readthedocs.io/en/stable/)
  - Spotify開発
  - Python製
  - 手続き型
- [Azkaban](https://azkaban.github.io/)
  - LinkedIn開発
  - Java製
- [Digdag](https://www.digdag.io/)
  - Treasure Data開発
  - Java製
  - DAG型
- [Google Cloud Dataflow](https://cloud.google.com/dataflow/)
- [Microsoft Azure Data Factory](https://azure.microsoft.com/ja-jp/services/data-factory/)
- [AWS Data Pipeline](https://aws.amazon.com/jp/datapipeline/)
- [Jenkins](https://www.jenkins.io/)

### パイプラインの記述スタイル

- 宣言型
  - XMLやJSONなどで実行したい内容を記述する
- 手続き型
  - プログラムに組み込む形で記述する
- DAG(Directed Acyclic Graphs)型
  - ノードとノードが矢印で結び付いたデータ構造に基づいたプログラミングモデルで記述する
  - → 手続き型でDAGを使用した記述

## References

- [データ基盤とは？種類と用途、データパイプラインとワークフロー管理 | AIdrops](https://www.bigdata-navi.com/aidrops/1183/)
- [3.データ分析を成功へと導くデータパイプライン：Pentaho：日立](https://www.hitachi.co.jp/products/it/bigdata/platform/pentaho/article/data-pipeline/data-pipeline.html#dsp_img)
- [第9回［最終回］　データパイプラインのためのワークフロー管理：これなら使える！ビッグデータ分析基盤のエコシステム｜gihyo.jp … 技術評論社](https://gihyo.jp/dev/serial/01/bigdata-analysis/0009)
