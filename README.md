# soccer-management-system

## 1.システム概要
本システムは、サッカーチームの運営を効率化するためのWebアプリケーションです。
第一段階では ユーザー管理機能 を中心に構築し、将来的に出席管理やスケジュール管理へ拡張可能な設計としています。

## 2.技術スタック
- フロントエンド: React + AWS Amplify
- バックエンド: AWS Lambda + API Gateway
- データベース: DynamoDB
- 認証/認可: Amazon Cognito
- ホスティング: Amplify Hosting

## 3. 機能一覧
ユーザー管理
- ユーザー一覧取得（誰でもアクセス可能）
- ユーザー詳細取得（認証済みユーザー）
- ユーザー作成（管理者のみ）
- ユーザー編集（管理者のみ）
- ユーザー削除（管理者のみ）
将来的な拡張
- 出席管理（試合・練習ごとの参加記録）
- スケジュール管理（試合日程、練習予定）
- 管理者ダッシュボード

## 4. API設計

| エンドポイント       | メソッド | 機能           | アクセス権限   |
|----------------------|----------|----------------|----------------|
| `/users`             | GET      | ユーザー一覧取得 | 公開           |
| `/user-info/{id}`    | GET      | ユーザー詳細取得 | 認証済み       |
| `/create-user`       | POST     | ユーザー作成     | 管理者         |
| `/update-user/{id}`  | PUT      | ユーザー編集     | 管理者         |
| `/delete-user/{id}`  | DELETE   | ユーザー削除     | 管理者         |

---

## 5. データベース設計（DynamoDB）

**テーブル名**: `usersTable`  
**主キー**: `userId` (string, UUID)

| 属性名             | 型      | 説明               |
|--------------------|---------|--------------------|
| `userId`           | string  | ユーザーID（主キー） |
| `name`             | string  | 氏名               |
| `email`            | string  | メールアドレス       |
| `teamId`           | string  | チーム識別子         |
| `jerseyNumber`     | number  | 背番号             |
| `hasRefereeLicense`| boolean | 審判資格有無         |

## 6. アクセス制御
- Cognitoによる認証
- グループ分け：
- admin → 作成・編集・削除可能
- user → 閲覧のみ

## 7. 開発フロー
- Amplifyプロジェクト初期化
- Auth（Cognito）追加
- Storage（DynamoDB）追加
- API（REST）追加
- Lambda関数実装
- フロントエンド統合（React）
- デプロイ（Amplify Hosting）







