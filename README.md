# learning-aws-css

[AWS Certified Security - Specialty](https://github.com/fujiokayu/learning-aws-css) の試験勉強用のリポジトリです。

<!-- TOC -->

- [learning-aws-css](#learning-aws-css)
  - [[試験ガイド](https://d1.awsstatic.com/ja_JP/training-and-certification/docs-security-spec/AWS-Certified-Security-Specialty_Exam-Guide.pdf)](#試験ガイドhttpsd1awsstaticcomja_jptraining-and-certificationdocs-security-specaws-certified-security-specialty_exam-guidepdf)
  - [学習用コンテンツ](#学習用コンテンツ)
    - [[サンプル問題](https://d1.awsstatic.com/ja_JP/training-and-certification/docs-security-spec/AWS-Certified-Security-Speciality_Sample-Questions.pdf)](#サンプル問題httpsd1awsstaticcomja_jptraining-and-certificationdocs-security-specaws-certified-security-speciality_sample-questionspdf)
    - [[AWS Certified Security - Specialty 公式練習問題集(Official Practice Question Set)](https://explore.skillbuilder.aws/learn/course/external/view/elearning/12551/aws-certified-security-specialty-practice-question-set-scs-c01-japanese?ss=sec&sec=prep)](#aws-certified-security---specialty-公式練習問題集official-practice-question-sethttpsexploreskillbuilderawslearncourseexternalviewelearning12551aws-certified-security-specialty-practice-question-set-scs-c01-japanesesssecsecprep)
    - [[公式トレーニング](https://explore.skillbuilder.aws/learn/course/762/exam-readiness-aws-certified-security-specialty-japanese)](#公式トレーニングhttpsexploreskillbuilderawslearncourse762exam-readiness-aws-certified-security-specialty-japanese)
      - [インシデントへの対応](#インシデントへの対応)
      - [ログと監視](#ログと監視)
      - [インフラストラクチャのセキュリティ](#インフラストラクチャのセキュリティ)
      - [ID 及びアクセス管理](#id-及びアクセス管理)
      - [データ保護](#データ保護)

<!-- /TOC -->

## [試験ガイド](https://d1.awsstatic.com/ja_JP/training-and-certification/docs-security-spec/AWS-Certified-Security-Specialty_Exam-Guide.pdf)

- 対象者
  - IT セキュリティに関してセキュリティソリューションの設計と実装における 5 年以上の経験
  - AWS ワークロードのセキュリティ保護における 2 年以上の実務経験
- 推奨される AWS に関する知識
  - AWS の責任共有モデルとそのアプリケーション
  - AWS のワークロードのセキュリティ管理
  - ログ記録戦略とモニタリング戦略
  - クラウドセキュリティの脅威モデル
  - パッチ管理とセキュリティの自動化
  - サードパーティーのツールやサービスで AWS セキュリティサービスを強化する方法
  - BCP とバックアップを含む災害対策管理
  - 暗号化
  - アクセスコントロール
  - データ保持

- 試験内容の概要
  - 第 1 分野: インシデントへの対応 12%
  - 第 2 分野: ログ記録とモニタリング 20%
  - 第 3 分野: インフラストラクチャのセキュリティ 26%
  - 第 4 分野: アイデンティティ管理とアクセス管理 20%
  - 第 5 分野: データ保護 22%

## 学習用コンテンツ

### [サンプル問題](https://d1.awsstatic.com/ja_JP/training-and-certification/docs-security-spec/AWS-Certified-Security-Speciality_Sample-Questions.pdf)

- 腕試しには以下の Official Practice Question Set を使用した方が良い
- 初見で7割解けたが、Official Practice Question Set の方が問題の難易度は遥かに高い

### [AWS Certified Security - Specialty 公式練習問題集(Official Practice Question Set)](https://explore.skillbuilder.aws/learn/course/external/view/elearning/12551/aws-certified-security-specialty-practice-question-set-scs-c01-japanese?ss=sec&sec=prep)

### [公式トレーニング](https://explore.skillbuilder.aws/learn/course/762/exam-readiness-aws-certified-security-specialty-japanese)

#### インシデントへの対応

- 以下の方法を知っている必要がある
  - AWS への不正使用の通知に応じて、侵害されたインスタンスや漏洩したアクセスキーの特定
  - インシデント対応計画に適切な AWS サービスが含まれていることを確認
  - 自動アラートの設定内容を評価し、セキュリティ関連のインシデントや問題への対策を講じる
- インシデント発生時、特定のインスタンスをネットワークから切り離す時はセキュリティ・グループの変更で対応する
  - インスタンスを終了することで影響を止めることはできるが、調査ができなくなる
- インシデント対応向けのサービス
  - AWS Trusted Advisor
  - AWS CloudFormation
  - AWS ServiceCatalog
  - VPC フローログ
    - 送信元と送信先の IP アドレス、ポート、プロトコル、開始時刻と終了時刻、パケット数とバイト数、アクションをキャプチャする個々のレコードで構成されるログ
  - AWS Config
  - Amazon API Gateway
  - AWS CloudTrail
  - Amazon CloudWatch
- インシデントの兆候
  - ログとモニタリング
  - 請求の記録
  - 脅威インテリジェンス
  - AWS サポート
  - パブリックレスポンス
- IAM アクセスキーが漏洩した場合
  - 認証情報を無効化する
  - 侵害された認証情報がアタッチされたユーザーに、IAM を拒否するポリシーをアタッチする
    - さらに、残っているセッションを全て取り消す
  - アクセスキーが関連づけられているユーザーを確認する
    - アクセスキーに関連づけられているポリシーの範囲を調べる
  - CloudTrail と AWS Config を使用して何か変更していないかを確認する
    - 他のキーや認証情報が漏洩していないかを最後に確認する
- AWS GuardDuty
  - CloudTrail, DNS log, VPC flow log からデータを収集する
  - 悪意のある操作や不正な動作を継続的にモニタリングし、AWS アカウントとワークロードを保護
  - 脅威の可能性が検出されると、GuardDuty コンソールと CloudWacth にセキュリティ・アラートを配信

#### ログと監視

- 以下の方法を知っている必要がある
  - セキュリティモニタリングとアラートの設計と実装
  - セキュリティモニタリングとアラートのトラブルシューティング
  - ロギングソリューションの設計と実装
  - ロギングソリューションのトラブルシューティング
- モニタリング用の AWS サービス
  - Amazon CloudWatch
    - [How Amazon CloudWatch works](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/cloudwatch_architecture.html)
    - AWS 組み込みメトリクスとカスタムメトリクスをモニタリングする
    - サービスとアプリケーションのログファイルを収集して処理する
    - イベントを検出し、通知または自動応答により応答する
  - AWS Config
    - リソースの全設定変更について詳細情報を継続的にキャプチャする
    - コンプライアンス分析とセキュリティ分析を有効化
    - セキュリティを侵害するような設定変更を特定し、影響を軽減できる
  - AWS Inspector
    - 以下を含むサポートされているベースラインに基づいてスキャンを実行
      - CVE
      - CIS ベンチマーク
      - セキュリティのベストプラクティス
      - Network reachability
  - AWS CloudTrail
- Amazon Kinesis
  - リアルタイムのストリーミングデータを収集、処理、分析する
    - 取り込み
      - Amazon Kinesis Data Streams
      - Amazon Kinesis Data Firehose
        - コンテンツを直接ストレージに格納する
    - 解析
      - Amazon Kinesis Data Analytics
- Amazon Athena
  - S3 内のデータを標準 SQL で分析できるインタラクティブなクエリサービスを提供

#### インフラストラクチャのセキュリティ

#### ID 及びアクセス管理

#### データ保護
