# learning-aws-scs-c01

[AWS Certified Security - Specialty](https://aws.amazon.com/jp/certification/certified-security-specialty/) の試験勉強用のリポジトリです。

- [learning-aws-scs-c01](#learning-aws-scs-c01)
  - [試験ガイド](#試験ガイド)
  - [学習用コンテンツ](#学習用コンテンツ)
    - [サンプル問題](#サンプル問題)
    - [AWS Certified Security - Specialty 公式練習問題集(Official Practice Question Set)](#aws-certified-security---specialty-公式練習問題集official-practice-question-set)
    - [公式トレーニング](#公式トレーニング)
      - [インシデントへの対応](#インシデントへの対応)
      - [ログと監視](#ログと監視)
      - [インフラストラクチャのセキュリティ](#インフラストラクチャのセキュリティ)
      - [ID 及びアクセス管理](#id-及びアクセス管理)
      - [データ保護](#データ保護)

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

### 書籍による学習

[要点整理から攻略する『AWS認定 セキュリティ-専門知識』](https://www.amazon.co.jp/dp/B08DCLRHC7/ref=dp-kindle-redirect?_encoding=UTF8&btkr=1)を購入。  
ただし2020年の本なので、直近2年にリリースされたサービスや変更点はカバーされていない。  
コントロールタワーなども対応していないので、新しいサービスは個別に公式ドキュメントを読み込む必要がある。

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
- 収集するのは
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

- 以下の方法を知っている必要がある
  - AWS のエッジセキュリティの設計
  - セキュアなネットワークインフラストラクチャの設計と実装
  - セキュアなネットワークインフラストラクチャのトラブルシューティング
  - ホストベースのセキュリティの設計と実装
- エッジセキュリティ用の AWS ツール
  - [Amazon Route 53](https://aws.amazon.com/jp/route53/)
    - DNS サービス
    - 他の AWS サービスと連携するように設計できる
  - [AWS WAF](https://aws.amazon.com/jp/waf/)
  - [Amazon CloudFront](https://aws.amazon.com/jp/cloudfront/)
    - CDN
  - [AWS Shield](https://aws.amazon.com/jp/shield/)
    - ネットワークおよびトランスポートレイヤーを防御
- AWS WAF の条件
  - SQLi や XSS のような一般的な攻撃パターンをブロックするカスタムルールや、特定のアプリケーションのために設計されるルールを作成できる
  - リクエストを許可またはブロックする基準
    - クロスサイトスクリプティングの一致
    - IP の一致
    - 地理的な一致
    - サイズの制約
    - SQL インジェクションの一致
    - 文字列の一致
    - 正規表現の一致
- DDoS 攻撃を軽減するための AWS ツール
  - Amazon Route 53
  - Amazon CloudWatch
  - AWS WAF
  - [Elastic Load Balancing](https://aws.amazon.com/jp/elasticloadbalancing/)
  - Amazon CloudFront
  - Amazon API Gateway
  - [AWS Shield](https://aws.amazon.com/jp/shield/)
  - [Amazon EC2 Auto Scaling](https://aws.amazon.com/jp/ec2/autoscaling/)
- ネットワーク ACL
  - サブネットレベルで作成、管理される
  - ステートレスなトラフィックフィルター
  - リストを拒否、または許可するためのルール
- セキュリティグループ
  - インスタンスの仮装 Fire Wall として機能
  - ステートフルな防御
  - Ingress ルールと egress ルールのみを許可する
  - 通信を許可するには設定が必要
- AMI のセキュリティに関する考慮事項
  - 安全でないアプリケーションを無効化
    - クリアテキストによる認証を使用したサービスとプロトコルを無効化
  - 漏えいを最小化
    - 必須でないネットワークサービスを起動時に無効化
    - 必要がない場合は、ファイル共有、Print Spooler、RPC などのデフォルトのサービスを無効化
  - AMI の作成時に認証情報を保護
    - ディスクと設定ファイルから AWS とサードパーティのすべての認証情報を削除
    - すべてのユーザー SSH パブリックキーペアとプライベートキーペアを削除
    - すべてのユーザーアカウントのパスワードを削除および無効化

#### ID 及びアクセス管理

- 以下の方法を知っている必要がある
  - AWS リソースにアクセスするためのスケーラブルな認証および認可システムの設計と実装
  - AWS リソースにアクセスするための許可および認証システムのトラブルシューティング
- AWS ではインバウンドおよびアウトバウンドの通信とネットワークトラフィックをより包括的にモニタリングできるよう、クラウドへのアクセスポイント数を制限しており、これらのユーザーアクセスポイントは API エンドポイントと呼ばれる
- API の保護
  - 署名によってアイデンティティを確認し、改ざん、リプレイ攻撃を防止している（署名にはタイムスタンプが含まれる）
- アクセスポリシーの種類
  - AWS 管理
  - カスタマー管理
  - インライン
- IAM アクセス許可の決定方法
  - ポリシーは AWS のエンティティであり、アイデンティティやリソースにアタッチして、これらのアクセス許可を定義する
  - AWS はユーザーなどのプリンシパルがリクエストを行ったときに、それらのポリシーを評価する
  - 複数の条件を指定したり、単一の条件に複数のキーを指定したりすると、IAM は論理 AND 演算を使用してそれらを評価する
    - 1 つのキーに複数の値を使用して単一の条件を指定すると、IAM は論理 OR 演算を使用して条件を評価する
  - アクセス許可が付与されるには、すべての条件を満たしている必要がある
- ポリシーエレメント
  - JSON ポリシードキュメントはエレメントで構成されており、エレメントには次の 5 つの主要な種類がある
    - Effect: ステートメントの結果を許可または明示的な拒否のどちらにするかを指定する
    - Action: 許可または拒否される動作を指定する
    - Resource: Action の対象となるリソースを指定する
    - Condition: 実行する際に満たす必要のある条件を指定する
    - Principle: ポリシーがアタッチされたリソースにアクセス可能なリソースを指定するリソースベースのポリシーや信頼ポリシーに使用する
- ポリシー管理におけるセキュリティの考慮事項
  - 必要なユーザーにのみアカウントを作成し、それ以外の場合はロールとフェデレーションを利用する
  - インラインポリシーではなくカスタマー管理ポリシーを使用する
  - 各 IAM エンティティには最小限の権限のみを付与する
  - さまざまなエレメントを使用してポリシーサイズを削減する
- AWS Directory Service
  - Microsoft Active Directory を AWS のサービスから使用するために利用できる方法が複数ある
    - AWS Managed Microsoft AD
      - Microsoft AD が AWS クラウド内に必要なケース
    - AD Connector
      - オンプレミスのユーザーが AD を介して AWS のサービスにアクセスする必要があるケース
    - Simple AD
      - 小規模で低コストな基本的な AD の機能を提供する

#### データ保護

- 以下の方法を知っている必要がある
  - キーの管理の設計と実装
  - キー管理のトラブルシューティング
  - 保管中のデータおよび転送中のデータのためのデータ暗号化ソリューションの設計と実装
- データ保護のための AWS サービス
  - Amazon RDS
  - Amazon DynamoDB
  - [AWS Secrets Manager](https://aws.amazon.com/jp/secrets-manager/)
  - [Amazon S3 Glacier](https://aws.amazon.com/jp/s3/storage-classes/glacier/)
  - [Amazon S3 Glacier Vault](https://docs.aws.amazon.com/amazonglacier/latest/dev/vault-lock.html)
- AWS Key Management Service
  - エンベロープ暗号化を使用した２層のキー階層
  - キーを一元的に管理し、セキュリティを保護
  - キーを使用できるユーザーを使用ポリシーで決定
  - 以下のことができる
    - ユニークなエイリアスと説明をつけたマスターキーを作成
    - マスターキーを自動的にローテート
    - キーの無効化、削除
    - CloudTrail を使用してキーの使用を監査
    - キーのインポート
  - キーの保護
    - リソースベースの権限
      - 一時的なアクセス権限、またはより詳細なアクセス権限
    - IAM ポリシーと類似した構文
      - カスタマーマスターキー (CMK) をプログラムで委任する
    - キーの管理、および暗号化/復号を行えるユーザーを指定
      - アクセスを許可するのに使用
- 転送中のデータ保護
  - クライアントとサービスエンドポイント間は TLS
  - パブリックキーインフラストラクチャ内で X.509 を使用
  - 証明書よりサーバーのアイデンティティを検証し、改ざんや偽造を防止
- AWS Certificate Manager
  - パブリックとプライベート両方の証明書を管理
  - 証明書のデプロイや自動更新を容易にする
- クライアント側の暗号化とサーバー側の暗号化
  - CSE 暗号
    - AWS に送信する前にユーザーがデータを暗号化する
    - データは暗号化された状態で保存
    - ユーザーのみが知っているキーとアルゴリズム。
  - SSE 暗号
    - 受信した後に AWS がユーザーに代わってデータを暗号化する
    - エンドユーザーに対して透過的
    - AWS は定期的にマスターキーをローテーションする
- Amazon S3 のデータアクセス保護
  - オブジェクト ACL
    - 個々のオブジェクトへのアクセス権限を付与
    - 別のアカウントが所有するオブジェクトにアクセスする
  - バケット ACL
    - ログ配信グループにバケットへの書き込みアクセスを付与する
  - バケットポリシー
    - バケット ACL よりも幅広いアクセス権限を付与する
    - バケットへのクロスアカウントアクセスを許可する
  - IAM ユーザーポリシー
    - ユーザーとグループを作成し、ポリシーをアタッチすることでアクセス権限を管理する
- ブロックパブリックアクセス
  - [Blocking public access to your Amazon S3 storage](https://docs.aws.amazon.com/AmazonS3/latest/userguide/access-control-block-public-access.html)
  - 任意のアクセスコントロールリスト (ACL) を介して許可されたバケットとオブジェクトへのパブリックアクセスをブロックする
- Amazon RDS のデータ保護
  - 転送中の保護
    - TLS とネイティブ暗号化クライアントを使用
    - Amazon RDS がアクセス認証を処理
  - 保管中の保護
    - AES-256
    - DB 作成時に有効にする必要がある（後から有効化はできない）
    - 特定の DB エンジンで TDE をサポート
- Amazon  DynamoDB のデータ保護
  - 転送中の保護
    - TLS で暗号化されたエンドポイントを使用
    - HMAC-SHA256 署名つきのリクエストのみを許可
  - 保管中の保護
    - CSE または SSE 暗号化オプションをサポート
      - SSE だと AES-256
    - テーブルとインデックスを暗号化
- Amazon S3 Gracier
  - デフォルトで暗号化
  - S3 のライフサイクルルールでも転送できる
  - データ取得後24時間使用が可能
  - データは一括、またはセグメント単位で取得が可能
  - ボールトロック
    - 時間ベースの保持
    - MFA 認証のサポート
    - ロック後はポリシーの変更不可
    - Write Once Read Many のサポート
- AWS Secrets Manager
  - ライフサイクルを通じてデータベース認証情報、API キー、その他のシークレットを簡単にローテーション、管理、取得する
  - シークレットの安全なローテート
  - アクセスの管理
  - 一元的なセキュリティと監査
  - 従量課金制

## 書籍で補足する知見

### インフラストラクチャのセキュリティ

- [Managing the AWS accounts in your organization](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_accounts.html)
  - SCP や OU について以下で補足する
- AWS Orgnizations
  - ルートと呼ばれるマスターアカウントとそれに紐づくメンバーアカウントの２種類のアカウントがある
  - OU という組織単位で管理し、上位階層の OU の設定は下位の OU に引き継がれる
  - サービスコントロールポリシー（SCP）
    - AWS サービスの利用可否を設定し、OU 単位で適用する
    - ルートにも適用できるが、将来的に弊害となる恐れがあるのでルートより下で設定するのが良さそう
    - 別途 IAM ポリシーを設定されている場合、IAM と SCP の両方で許可されているものだけが利用可能となる
- AWS WAF
  - v1 では10ルールまでだったが、2019/11以降はWAF Capacity Unit という単位に変更され、より複雑な設定が可能になった
- AWS  Shield
  - Standard ではネットワーク層およびトランスポート層の一般的な DDoS 攻撃に対処
  - Advance ではさらに高度な攻撃や DDoS によるコスト増に対処し、かつ、専門チームのサポートが受けられる
    - アノマリー検知ができる
- AWS Firewall Manager
  - AWS WAF、AWS Shield Advanced、Amazon VPC Security Group を一元管理するためのサービス
  - あらかじめルールを作っておくことによって新たなアプリやリソースに適用できる
  - AWS Organization と統合されているので、複数のアカウントに跨って操作できる
- Amazon Route 53
  - DNS サービスだが、単純な名前解決だけではなく
  - ヘルスチェックを設定しておくことで、フェイルオーバールーティングを使って異常時に Sorry ページへルーティングすることもできる
  - 位置情報ルーティングを使って大陸別、国別のルーティングを行うことができる
    - セキュリティを目的にサービスを展開していない国からのアクセスを弾いたりもできるのか
  - レイテンシーが最小になるようにルーティングすることができる
  - 加重ルーティングによってリクエスト全体の中から一定の割合のみ別の向き先へルーティングする、といったこともできる
- Amazon CloudFront
  - 静的データ、動的データを高速に配信するための CDN サービス
  - AWS 内の origin とエッジ間でのデータ転送は無料
  - origin が S3 の場合、CloudFront に Origin Access Identity という特別なユーザー設定をすることで、S3 はそこからの読み取りだけを許容するように設定できる
    - 最近だと Managed Prefix を使うはず
- Elastic LoadBalancing
  - Application LoadBalancer
    - レイヤー7で動作
    - VPC に属する EC2、コンテナ、IP アドレス、Lambda を指定できる
    - 急激なトラフィック増加に対してスケールが間に合わない時がある
  - Network LoadBalancer
    - レイヤー4で動作
    - VPC に属する EC2、コンテナを指定できる
    - 急激なトラフィック増加にも対応
  - Classic LoadBalancer
    - レイヤー4と7の両方で動作
    - EC2-Classic と VPC の両環境で動作する
      - 基本的に EC2-Classic で使われることを想定しており、VPC 環境では ALB か ELB が推奨されている
  - ALB と CLB は動的に IP が割り当てられるので、DNS 名が必要になる
  - ALB と CLB はセキュリティ・グループが使用可能
- [AWS AutoScaling](https://aws.amazon.com/jp/autoscaling/)
  - EC2、Spot Fleet、ECS タスク、DynamoDB のテーブルとインデックス、Aurora のレプリカが対象
  - CloudWatch メトリクスの増減のほか、スケジュールされたスケールや学習によって予測したスケーリング機能がある
  - 総数を維持する設定では、障害によって動作しないインスタンスが発生したら追加することが可能
- Security Group
  - インスタンスに対するトラフィックへのアクセス制御を行う
  - 一つのインスタンスには複数の Security Group を割り当てられる
  - Network ACL は VPC サブネット間の通信を制御する機能であり、サブネット間通信の場合は SG と NACL の両方で許可されている必要がある
    - Network ACL はステートレスであるため、往路と復路両方の通信をそれぞれのサブネットで許可しておく必要がある
- [AWS Artifact](https://aws.amazon.com/jp/artifact/)
  - AWS のセキュリティおよびコンプライアンスレポート(AWS Artifact Report)と特定のオンライン契約にオンデマンドでアクセスできる
  - AWS Artifact Report
    - サードパーティーの監査人による AWS の監査レポートのダウンロードサービス
    - このレポートを利用するには AWS との事業提携契約、秘密保持契約を受諾する必要がある
  - AWS Artifact Agreement
    - AWS と BAA などの契約を締結するためのサービス
- [AWS Control Tower](https://aws.amazon.com/jp/controltower)
  - ブループリントベースでマルチアカウントの AWS 環境のセットアップを自動化
  - ガードレールと呼ばれる必須の、強く推奨されている高レベルルールを提供し、これがサービスコントロールポリシー (SCP) を使用
  - AWS Config とも連携

### データ保護

- AWS Key Management Service
  - 鍵の使用履歴は全て CloudTrail に保存される
  - エンベロープ暗号化という仕組みで暗号化を行っており、データを暗号化するための Customer Data Key(CDK) とデータキーを暗号化するための Customer Master Key(CMK)を使うことになる
    - CMK で暗号化できるのは 4KB まで
    - リージョン間で CMK の共有はできない
  - カスタマー管理、AWS 管理、AWS 所有の３種類の CMK がある
    - カスタマー管理 CMK
      - AWS 利用者が作成、所有、管理する。1年ごとの自動ローテーションを有効、無効を設定可能
    - AWS 管理 CMK
      - 3年ごとに AWS 側で自動ローテーションされる
    - AWS 所有 CMK
      - AWS サービスが裏側で使っているもので、利用者が意識することはない
  - CMK は有効化、無効化、再有効化ができる
  - CMK の削除には7〜30日間の待機期間が設けられている
    - この間に使用されたかどうかは CloudWatchh や CloudTrail で確認できる
  - CMK をローテーションした後も、CMK はローテーション前のキー情報（バッキングキー）も保持しているため、古いデータも復号できる
  - 1年よりも短いサイクルでキーローテーションをしたい場合、手動ローテーションができる
  - Bring Your Own Key の機能で、ユーザーが作成したキーをインポートすることもできる
    - インポートできるのは 256bit 対象キー
    - 自動ローテートはできない
  - キーポリシーや IAM ポリシーを使ってアクセス制御が可能
  - キーポリシーを使用して、MFA を矯正することが可能
  - KMS の API リクエストにはレート制限があるため、1秒に1万回以上呼び出すとエラーになる
  - 2019/11 から非対称暗号もサポート
- [AWS CloudHSM](https://aws.amazon.com/jp/cloudhsm/)
  - KMS よりも高くてセキュアな高級鍵管理サービス。より厳格なコンプライアンスが求められるユーザー向け
  - 暗号化キーの保存に専用のハードウェアが使用されるため、鍵の内容は AWS も参照することはできない
  - VPC 内に配置する

### ログと監視

- Amazon CloudWatch
  - 最大15ヶ月保持
  - CloudWatch エージェントをインストールさえすればオンプレミスのサーバーでも使える
- AWS Config
  - こちらもオンプレミスでも使える。収集する対象のリソースは利用者が設定する
- AWS CloudTrail
  - AWS 操作が自動的に記録される
  - 管理イベント、データイベント、インサイトイベント（検知された異常なアクティビティ）があり、デフォルトで有効なのは管理イベント
  - ダイジェストを使った整合性検証ができる
- [AWS X-Ray](https://aws.amazon.com/jp/xray/)
  - アプリのサービス間リクエストを収集し、分析するためのサービス
  - 対象のアプリが X-Ray SDK を統合し、エージェントをインストールすることでキャプチャが可能になる
- [Amazon Inspector](https://aws.amazon.com/jp/inspector/)
  - Amazon EC2 と ECR のセキュリティ評価を行う
  - チェックルールはマネージドなものしか使用できない
- VPC Flow Logs
  - 送信元/先の IP、通信許可、遮断などのネットワークの基本情報が確認できる
  - CloudWatch と連携させてセキュリティ・アラートを実装するなど
  - パケット情報までは確認できないため、必要に応じてパケットキャプチャツールが必要
- [Amazon QuickSight](https://aws.amazon.com/jp/quicksight/)
  - DB や S3/Athena のデータをダッシュボードビューで可視化できる
  - Salesforce などの SaaS にも接続が可能
- Amazon Kinesis
  - Kinesis Data Streams
    - 大量のストリームデータをリアルタイム処理するためのサービス
  - Kinesis Data Firehose
    - ストリームデータを AWS データストア(S3, RedShift, Elastic)にロードするためのサービス
  - Kinesis Data Analytics
    - ストリームデータをリアルタイムで SQL 処理するためのサービス
  - Kinesis Video Streams
    - 動画データを AWS へストリーミングするためのサービス

### インシデント対応

- AWS Config
  - Config ルールという機能で各設定がルールに準拠しているかチェックできる
    - EBS が暗号化されているか、S3 がパブリックになっていないか、SSH がパブリックに開いてないか、など
    - マネージドルールとカスタムルールがある
  - Config ルールで非準拠となったリソースに対して、検知したタイミングで自動修復を行うことができる
    - この機能が出るまでは、CloudEvents で Lambda を呼び出して修正する、というパターンが使われていた
- AWS Systems Manager
  - EC2 やオンプレミスのサーバーを制御、管理するためのサービス
  - Run Command や Session Manager、Parameter Store などの複数の機能から構成されている
  - リソースを更新、管理、設定する場合は SSM Agent のインストールが必要
  - Inventory では SSM Agent がインストールされたサーバーにインストールされているソフトウェアを一覧表示できる
- AWS Trusted Advisor
  - コスト、パフォーマンス、セキュリティ、フォールトトレランス、サービス制限の5つの観点からチェックを行なってくれる
  - レポートは日次。リアルタイム検知を行いたい場合は CloudWatch と組み合わせる
  - Trusted Advisor のチェックに基づいて CloudWatch Events を設定することはできません。
- AWS CloudFormation
  - CloudFormation テンプレートを使った環境である場合、すぐにその環境のコピーが作れるのでインシデント対応時に再現環境がすぐに作れる
  - ドリフト検出機能で稼働中の環境とテンプレートの差分を検出できる
- Amazon Macie
  - S3 上の個人情報などの機密データを自動的に発見、通知、保護処理を行える
- Amazon GuardDuty
  - VPC Flow Logs、CloudTrail、DNS Logs をインプットにしている
- AWS Security Hub
  - セキュリティ状況やコンプライアンスの準拠情報を確認できる
- Amazon Detective
  - VPC Flow Logs、CloudTrail、GuardDuty などをインプットに、潜在的なセキュリティの問題や不審なアクティビティを分析、調査できるサービス
  - 過去のログやイベント情報といった時系列の観点を含み、グラフ化、可視化するという点で GuardDuty とは目的が異なる

## 模擬テストで補足する知見

- [DDoS シミュレーションテストポリシー](https://aws.amazon.com/jp/security/ddos-simulation-testing/)
  - DDoS シミュレーションには AWS Partner Network の協力が必要
- AWS CLI またはコンソールだけを使用して CMK をローテーションすることはできない
- Lambda 関数と EventBridge (CloudWatch Events) は、キーマテリアルをローテーションできない
- Organizations 内で組織証跡を設定すると、ログファイルの整合性検証を有効にできる
- Amazon Inspector は EC2 インスタンスのネットワークアクセシビリティと、インスタンスで実行されるアプリケーションのセキュリティ状態をテストする
  - Amazon Inspector はアプリケーションの露出、脆弱性、ベストプラクティスからの逸脱を評価する
  - ネットワーク到達可能性パッケージルールは、ネットワーク設定を分析して EC2 インスタンスのセキュリティ上の脆弱性を見つけます。
  - Amazon Inspector は EC2 インスタンスの脆弱性をチェックできますが、セキュリティグループへのアクセスは確認できません
- S3 バケットは IAM ロールを継承できない
- S3 オブジェクト所有権は、バケット所有者が他の AWS アカウントによってバケットにアップロードされたオブジェクトの所有権を自動的に継承できる S3 の機能
- [AssumeRoleWithSAML](https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRoleWithSAML.html)
  - IAM ポリシーは、SAML アサーションによって認証される IAM ロールに割り当てられる

## [AWS Black Belt Online Seminar](https://aws.amazon.com/jp/aws-jp-introduction/aws-jp-webinar-service-cut/#management-admin)

### [AWS Identity and Access Management (AWS IAM) Part1](https://www.youtube.com/watch?v=K7F5yTThynw)

### [AWS Identity and Access Management (AWS IAM) Part2](https://www.youtube.com/watch?v=qrZKKF6V6Dc)

## 追加の問題集

[1週間で攻略！AWS認定セキュリティ – 専門知識 本番用問題集 140問（65問 × 2セット + 10問） 詳解付き AWS認定本番用問題集シリーズ](https://amazon.co.jp/dp/B09RH137K4)

不正解である回答について何も言及がないのがやや不便

- ACM証明書をAmazonCloudFrontで使用するには、USEast（N.Virginia）リージョンで証明書をリクエストまたはインポートする必要があります。
- ActiveDirectoryでは、信頼関係によって様々なリソースへのアクセスが可能になりますが、この信頼関係には一方通行のものと双方向のものがあります。一方向の信頼とは、2つのドメイン間に作成される一方向の認証パスのことです。ドメインAとドメインBの間の一方通行の信頼関係では、ドメインAのユーザーはドメインBのリソースにアクセスできますが、ドメインBのユーザーはドメインAのリソースにはアクセスできません。一方通行の信頼関係には、作成される信頼関係の種類に応じて、非遷移的または遷移的なものがあります。
- すでにADインフラストラクチャを持っていて、AD対応のワークロードをAWSクラウドに移行する際にそれを使用したい場合、AWSManagedMicrosoftADが役立ちます。ADトラストを使用して、AWSManagedMicrosoftADを既存のADに接続することができます。これにより、ユーザーはオンプレミスのAD認証情報を使って、ユーザー、グループ、パスワードを同期することなく、AD対応のアプリケーションやAWSアプリケーションにアクセスすることができます。
- EC2 の EBS ボリュームが KMS で暗号化されている時に追加で必要になるパーミッション
  - "Condition":{"Bool":{"kms:GrantIsForAWSResource":true
  - 「Action」要素にkms:CreateGrant
- デフォルトでは、CloudTrailがユーザーのバケットに配信するログファイルは、AmazonS3が管理する暗号化キー（SSES3）を用いたAmazonサーバーサイド暗号化によって暗号化されます。
  - 直接管理可能なセキュリティレイヤーを提供するために、代わりにCloudTrailのログファイルにAWSKMS管理下の鍵によるサーバーサイド暗号化（SSEKMS）を使用することができます。
- AWSSecurityHub の CISAWSFoundationsBenchmarkは、AWSのセキュリティ構成のベストプラクティスをまとめたものです。業界で認められているこれらのベストプラクティスは、すでに提供されているハイレベルなセキュリティガイダンスを超えて、AWSユーザーに明確なステップバイステップの実装と評価の手順を提供します。
- (API で利用する際に)アカウントに割り当てられているAWS管理のCMKではなく、顧客管理のCMKを使用するには、keyidパラメータを使用してキーを指定する必要があります。
- AmazonCognitoのIdentityPoolは、ゲスト（未認証）のユーザーや、認証されてトークンを受け取ったユーザーに一時的なAWSクレデンシャルを提供します。
- AWSCloudHSMは、ユーザー自身のAmazonVirtualPrivateCloud（VPC）内で動作するため、AmazonEC2インスタンス上で動作するアプリケーションでHSMを容易に使用することができます。

## Web 学習

[AWS WEB問題集で学習しよう](https://aws.koiwaclub.com/paid-membership-registration/)
追加の問題集が Kindle で見るとレイアウトが大変微妙で手間がかかるので、これも試してみる。

Certified Security Specialty を受ける場合はプロフェッショナルプランで ¥5480(税抜)。
せっかくならついでに SAP も取りたくなるな・・・

- [AWS KMS のキーポリシー](https://docs.aws.amazon.com/ja_jp/kms/latest/developerguide/key-policies.html#key-policy-default-allow-root-enable-iam)
- アクセスキーの漏洩は Trusted Advisor で。
- AWS Direct Connect
  - AWS への専用ネットワーク接続を作成する
- CloudTrail は DynamoDB と統合されており、IP アドレス情報をもとに API 呼び出しを追跡できる
  - 一方で、CloudWatch は DevOps や SRE、マネージャー層のためのモニタリングを提供する
- ネットワーク ACL はステートレスです。アウトバウンドルールは、一時ポート 1024～65535に対して有効にする必要があります
- セキュリティグループはステートフルであり、インバウンドトラフィックに対してアウトバウンドルールを定義する必要がない
- EC2 インスタンスのメタデータにアクセスするには、ポート 80 の IPアドレス 169.254.169.254 へのアウトバウンド TCP が通信に必要です
- EC2 Runcommand でインスタンス上の authorized_keys を更新することで、SSH キーを変更することができます
- インポートされたキーマテリアルを使用した KMS キーは手動でローテーションする必要があります。手動ローテーションは、新しい KMS キーを使用してエイリアスを変更することで実行できます
- ボールトロックポリシーは、ボールトアクセスポリシーとは異なります。どちらのポリシーも、ボールトへのアクセスを制御します。ただし、ボールトロックポリシーでは、ロックによって変更を禁止することにより、コンプライアンス管理を強力に実施することができます。ボールトロックポリシーは、データへの詳細なアクセス制御が求められることの多い、規制やコンプライアンス管理のデプロイに使用できます。対照的に、ボールトアクセスポリシーでは、コンプライアンスと関係がなく、一時的で、頻繁に変更が発生しやすいアクセス制御を実装します。ボールトロックポリシーとボールトアクセスポリシーは同時に使用できます。たとえば、ボールトロックポリシーで時間ベースのデータ保持ルールを実装し (削除の拒否)、指定したサードパーティやビジネスパートナーに対して読み取り許可を付与することができます (読み取りの許可)
- AWS Systems Manager パラメータストアの SecureString パラメータは追加費用なしで使用できます。また、認証情報を監査することができます
- Amazon GuardDuty は IP ホワイトリストを許可しているため、この場合、Amazon GuardDuty はアラートを生成しません
- NACL を使用すると、セキュリティグループではできない IP アドレスからのアクセスを拒否することができます。また、NACL はサブネットレベルで機能し、セキュリティグループはインスタンスレベルで機能します。そのため、ポートスキャンはセキュリティグループに到着しません
- DynamoDB はデータの保存時の暗号化をサポートしています。テーブルの作成時に暗号化を有効にする必要があります。既存のテーブルでは暗号化を有効にできません
- Amazon Kinesis Data Streams は、保管中および転送中の暗号化を提供している
- CloudTrail の証跡は [Write-only] イベントフィルターで構成して、書き込み変更のみをプッシュすることができます
- もしSSL を使いたいが、ロードバランサーに SSL 終端処理をさせたくない場合（SSL オフロードとして知られている）、クライアントからロードバランサーへの接続に TCP を使用し、ロードバランサーからバックエンドアプリケーションへの接続に SSL プロトコルを使用し、リクエストを処理するバックエンドのインスタンスに証明書を配置することができます
- KMS キーはリージョンに制約されており、リージョンをまたいで複製したりコピーしたりすることはできないため、ターゲットリージョンの AWS サービスがターゲットリージョンのリソースを復号化できるように、ソースリージョンの AWS KMS と通信するように設定します。ただし、KMS キーにはクロスアカウントアクセスを付与することができます
- Amzon CloudWatch イベントは、StopLogging の CloudTrail イベントを監視し、Lambda 関数をトリガーしてロギングを再度有効にするように設定できます。また、CloudWatch イベントはリアルタイムであるためダウンタイムは最小限にできます
- SES SMTP: AWS は email-smtp.us-east1.amazonaws.com にポート 587 で接続することを推奨しています
- Amazon EFS は、ファイルシステムの 2 つの暗号化形式、「転送時の暗号化」と「保管時のデータの暗号化」をサポートします。Amazon EFS ファイルシステムを作成する場合、保管時のデータの暗号化を有効にすることができます。後でファイルシステムをマウントする時、伝送中のデータの暗号化を有効にすることができます
- 現在、パケット検査を提供するAWSサービスはなく、ホストまたはネットワークベースのサードパーティソリューションを使用することになります
- CloudTrail のログ配信は15分以内という制約があるため、迅速でリアルタイムな処理には向いていない
- VPC フローログと AWS Lambda を使って送信トラフィックを制限することはできません。プロキシは、フィルタリングと送信トラフィックを制限するために必要です
- オリジンアクセスアイデンティティ (OAI) を作成し、ディストリビューションに関連付ける必要があります。S3 バケットポリシーは、OAI からのアクセスのみを許可するように変更する必要があります
  - CloudFront は VPC エンドポイントで動作しない。VPC エンドポイントは、EC2 インスタンスから VPC 内の S3 にのみトラフィックをルーティング
- Auto Scaling を使用したアプリケーションは IP アドレスを使用して制御ができないため、セキュリティグループにセキュリティグループを関連付けることで制御することができます
  - セキュリティグループでは、接続元をネットワークアドレスで許可することができますが、その替わりに他のセキュリティグループで許可することもできます
- awsvpc を使用すると、コンテナのセキュリティを強化するタスクネットワーキング機能を提供します。また、IAM ロールは、IAM ベストプラクティスに従ってタスクに割り当てることができます
- セキュリティグループとネットワーク ACL のルールは、「送信先 IP」、「プロトコル」、「ポート範囲」のみで、URL ベースのルールを作成することはできません。したがって、VPC にウェブプロキシサーバーを設定し、アウトバウンドアクセスの URL ベースのルールを実施します。そしてデフォルトルートを削除します。
- CloudWatch エージェントの awslogs が実行されていない、権限の問題、 awslogs が CloudWatch に接続できない、ログファイルのフィンガープリントの問題、タイムスタンプの問題など、さまざまな問題が考えられます
- アベイラビリティーゾーンは、すべて 100 km 以内 (互いに 60 マイル) に配置されている
- Amazon Cognito が SAML アサーションを受信すると、SAML 属性をユーザープール属性にマッピングできる必要があります。Amazon Cognito が ID プロバイダから SAML アサーションを受信するように設定する場合、ID プロバイダーが Amazon Cognito を証明書利用者として持つように設定されていることを確認する必要があります。Amazon API Gateway は、Amazon Cognito から渡される認証を理解できる必要があります
- 一定期間経過したアクセスキーを検知するようなサービスはないため、自前でスクリプトを組む必要がある
- IAM ポリシーを使用して、タグ付けされた AMI からのみ EC2 インスタンスを起動するようにユーザーまたはサービスを制限できます。また、AWS Config を使用して、未承認の AMI で起動されたインスタンスをチェックするルールを定義できます
- VPC フローログはポートスキャンのキャプチャに役立ち、AWS Lambda を使用して通知をトリガーすることができます。Amazon GuardDuty は基本的にこれらのサービスを統合します
- ルートテーブルは受信トラフィックを制御せず、送信トラフィックのみを制御する
- AWS WAF の ウェブ ACL のレートベースのルールは、正当なトラフィックに影響を与えることなく不要なトラフィックを減らすリクエスト数を制限するために CloudFront ディストリビューションに設定することができます。
- AWS KMS では、キーポリシーおよび許可という 2 つのアクセスコントロールメカニズムをサポートしています。許可を利用すると、AWS KMS keys (KMS キー) の使用を他の AWS プリンシパルにプログラムによって委任できます。これらを使用してアクセスを許可できますが、拒否することはできません。許可は限定的であり、作成と取り消しが容易であるため、一時的なアクセス許可やより詳細なアクセス許可を付与するためによく使用されます。
- aws:SourceVpce とプライベート DNS による VPC エンドポイントの作成
- Network Load Balancer と Gateway Load Balancer はリダイレクトをサポートしていない
- restricted-ssh の AWS Config マネージドルールは、セキュリティグループを通じて SSH トラフィックが有効になっているかどうかを確認して通知するために作成することができる
- Network Load Balancer に TCP リスナーを設定して、TLS トラフィックをコンテナに通過させることで、復号化を処理し、最も低いレイテンシーで安全なエンドツーエンドの暗号化を実現します
- インポートされたキーは、いつでもデータを削除または消去する能力を提供するため、KMS キーでインポートされたキーマテリアルを使用します
- Amazon Kinesis Data Firehose はセキュリティチームアカウントで作成でき、CloudWatch Logs サブスクリプションフィルターは各アカウントで作成して Amazon Kinesis Data Firehose と Amazon S3 にログを送信できます。
  - 別の AWS アカウントの所有者と協力して、Amazon Kinesis または Amazon Kinesis Data Firehose ストリームなどのご自身の AWS リソースで相手のログイベントを受信することができます (これをクロスアカウントデータ共有と言います)。たとえば、このログイベントデータを集中管理型の Kinesis または Kinesis Data Firehose ストリームから読み取り、カスタム処理や分析を実行することができます。カスタム処理は、多数のアカウントが協力しデータを分析する場合に特に便利です。
- [IAM ロールの一時的なセキュリティ認証情報の取り消し](https://docs.aws.amazon.com/ja_jp/IAM/latest/UserGuide/id_roles_use_revoke-sessions.html)
- DynamoDB 暗号化クライアントは、クライアント側の暗号化をサポートし、テーブル項目に署名して、保存中および転送中の暗号化を保証します。
- AWS PrivateLink は、アプリケーションを公開することなく、他の AWS アカウントにプライベートエンドポイントを提供します。このアプローチは、アプリケーションへのアクセスを、他の子会社の AWS アカウントが接続できるプライベートエンドポイントのみに制限することができるため、よりスケーラブルで安全です。
- セキュリティグループとネットワーク ACL ルール
  - 1行目の ACCEPT は、トラフィックが NACL およびセキュリティグループによって受け入れられたことを示しています。2行目の REJECT は、ステートレスである NACL からの拒否を示します。したがって、VPC の NACL で、アウトバウンドの ICMP トラフィックを許可することで、Ping を動作させることができます。