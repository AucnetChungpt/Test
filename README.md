## AWS Lambda

### **概要**

- **AWS Lambda**: AWS のサーバーレスサービスで、サーバーを管理せずにコードを実行可能
- **メモリ**: 128MB から 10GB まで。
- **最大実行時間**:  Lambda functionの実行時間は最大 15 分。

### **主な特徴**

- **サーバーレス**:
  - サーバー管理不要で、アプリケーションのロジックに集中可能。
  - AWS がメモリ、CPU、コードのデプロイ、ネットワークなどを管理。
- **イベント駆動型**: Lambda は AWS の各サービス（S3、DynamoDB、API Gateway など）からのイベントでトリガーされる。
### **主要コンポーネント**
 - Lambda Function: ロジックを処理する場所。
 - Event Source: Lambda をトリガーするイベントの発生元。

### **動作の仕組み**

-  Lambda 関数を作成（設定とソースコードを含む）。
- AWS サービスからのイベントを通じて Lambda をトリガー。
- コードを実行: AWS が自動でリソースを割り当ててコードを実行。

### **Lambda functionの構成**

- **ソースコード:**:
  - Python、Node.js、Java、C#、Go などの多言語をサポート。
  - AWS Management Console 上で直接記述するか、ZIP ファイルまたはコンテナイメージでデプロイ。
- **入力イベント**: トリガー元からデータを受信、例：
  - S3 に新しいファイルがアップロードされた場合。
- **実行環境**: AWS がランタイムと標準ライブラリを提供。

### **Lambda の利用例**

-  ファイル処理: S3 にアップロードされた画像を自動リサイズ。
-  API バックエンド: API Gateway と組み合わせてサーバーレスなバックエンドを構築。

### Lambda をトリガーするソース:

- Amazon S3: ファイルのアップロード/削除時。
- Amazon DynamoDB: テーブルの変更時。
- Amazon API Gateway: HTTP/HTTPS リクエスト時

### 実行:

- Lambda 関数を作成。
- "Create function" を選択して設定を行う。
- 関数をトリガー: S3、API Gateway、または CloudWatch からイベントを作成してトリガー。
- ログを確認。


<h5 style="border: 0.1px solid lightgray;">

## DynamoDB
### **概要**
- サーバーレスの NoSQL データベースサービス。
### **構成**

- テーブル → アイテム → 属性: キーと値の形式でデータを保存。
- Primary Key:
  - Partition Key: 各アイテムを一意に識別。
  - Composite Key:  Partition Key と Sort Key 組み合わせでデータを整理

### **主な機能**

- **スケーラビリティとパフォーマンス**:
   - 読み取り/書き込みの自動スケーリング
   - Hỗ trợ Provisioned Mode と On-Demand Mode をサポート
- **ストリーム**: テーブルの変更を記録し、Lambda などのアプリケーションをトリガー。
- **TTL (Time to Live)**: 古い項目を自動削除。
- **Backup & Restore**: テーブル全体のオンデマンドバックアップや自動バックアップ（継続的バックアップ）。
- **Bảo mật**:
   - 保存データの暗号化 (at-rest).
   - AWS IAM による権限管理。

### **メリット**

- 低レイテンシーでスケールが容易。
- Lambda、S3、API Gateway との高い互換性。


<h5 style="border: 0.1px solid lightgray;">

## API Gateway

### **概要**

- API リクエストを受信して処理するサービス。
- Fully managed service, RESTful API と WebSocket API をサポート。

## **主な特徴**

- 需要に応じて自動スケーリング。
- Throttle:
  - Rate: 秒ごとの最大リクエスト数（1 秒間）。
  - Burst: 一度に許可される最大リクエスト数。
  - 制限超過時のエラー: *429 - Too Many Requests*。
- サーバーレスバックエンド:
  - Lambda と連携してサーバーレスな API を作成。
  - IAM ロールや AWS Cognito を使用してアクセス権を管理。

## **実行**

1. AWS コンソールで API を作成。
   - RESTful API または WebSocket API を選択。
   - メソッド（PUT、POST など）を設定。
2. Lambda または EC2 と接続。
   - Lambda 関数を作成し、API Gateway と接続。
   - API をデプロイしてリクエストを受け取れるようにする。

<h5 style="border: 0.1px solid lightgray;">

## Cognito

### **概要**

-　Web およびモバイルアプリのユーザー認証と管理サービス。
- AWS やサードパーティサービス（Facebook、Google、Apple）と統合可能。

### **主な機能**

- ユーザー認証:
   - 登録、ログイン。
   - MFA（二要素認証）をサポート。
   - サードパーティサービス（Facebook、Google、Apple）経由での認証。
- ユーザー管理:
   - User Pool:ユーザー情報を保存。
   - Identity Pool: AWS サービスへのアクセス権を付与。

管理画面からユーザーの確認、パスワード変更、アカウントロックなどをサポート。