 ポケット勤怠 | Attendance Management System

[![TypeScript](https://img.shields.io/badge/TypeScript-4.9.5-blue.svg)](https://www.typescriptlang.org/)
[![React](https://img.shields.io/badge/React-18.2.0-blue.svg)](https://reactjs.org/)
[![Express](https://img.shields.io/badge/Express-4.18.2-green.svg)](https://expressjs.com/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-14.x-blue.svg)](https://www.postgresql.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

ポケット勤怠は、従業員の出退勤記録、休暇申請、勤怠レポートを管理するためのウェブアプリケーションです。

従業員・管理者・スーパー管理者それぞれの利用シーンを想定し、ロールベースのアクセス制御、企業単位の設定管理、勤怠・休暇情報の集約、部門別レポート、コンプライアンス確認までをカバーします。日々の勤怠管理を効率化するとともに、管理者が必要な情報を把握しやすい業務基盤として利用できることを重視しています。

### 🎯 主な目的 | Goals

- **勤怠業務の効率化** — 出退勤・休暇・レポートを一元管理
- **管理業務の可視化** — 個人・部門単位で勤怠状況を確認
- **コンプライアンス対応** — 残業・休憩・休日・深夜労働などを確認
- **安全な権限管理** — ユーザーの役割に応じて操作範囲を制御
- **将来の拡張性** — API・サービス層・データモデルを分離し、機能追加しやすい構成

![スクリーンショット 2025-03-16 0 58 26](https://github.com/user-attachments/assets/a7a4e016-61bd-4831-9d98-0a2acfbc9755)

*This is a web application for managing employee attendance records, leave requests, and attendance reports.*

## 📑 目次 | Table of Contents

- [機能 | Features](#機能--features)
- [技術スタック | Tech Stack](#技術スタック--tech-stack)
- [開発環境のセットアップ | Development Setup](#開発環境のセットアップ--development-setup)
- [使用方法 | Usage](#使用方法--usage)
- [プロジェクト構造 | Project Structure](#プロジェクト構造--project-structure)
- [テスト | Testing](#テスト--testing)
- [トラブルシューティング | Troubleshooting](#トラブルシューティング--troubleshooting)
- [貢献 | Contributing](#貢献--contributing)
- [ライセンス | License](#ライセンス--license)

## 機能 | Features

- **ユーザー認証 | User Authentication**
  - サインアップ/ログイン | Sign up/Login
  - ロールベースのアクセス制御（一般従業員/管理者/スーパー管理者） | Role-based access control (Employee/Admin/Super Admin)

- **企業管理 | Company Management**
  - 企業の作成・編集・削除（スーパー管理者のみ） | Create/Edit/Delete companies (Super Admin only)
  - 企業固有の設定管理 | Company-specific settings management
  - 複数企業の管理（スーパー管理者） | Multi-company management (Super Admin)

- **勤怠記録 | Attendance Records**
  - 出勤/退勤の打刻 | Clock in/out
  - 勤務時間の自動計算 | Automatic working hours calculation
  - 勤怠履歴の表示 | View attendance history

- **休暇管理 | Leave Management**
  - 休暇申請の作成 | Create leave requests
  - 休暇申請の承認/却下 | Approve/reject leave requests
  - 休暇履歴の表示 | View leave history

- **レポート | Reports**
  - 個人の勤怠レポート | Individual attendance reports
  - 部門別の勤怠レポート | Department-wise attendance reports
  - コンプライアンスレポート | Compliance reports
    - 残業時間監視 | Overtime monitoring
    - 休憩取得状況 | Break time compliance
    - 休日労働監視 | Holiday work monitoring
    - 深夜労働監視 | Night work monitoring
    - 有給休暇取得状況 | Paid leave usage tracking
  - レポートのエクスポート | Export reports

## 技術スタック | Tech Stack

本プロジェクトは、型安全なフロントエンドとAPIバックエンド、リレーショナルデータベースを組み合わせた一般的なWebアプリケーション構成です。状態管理・データフェッチ・入力バリデーションなどの責務を分離し、開発・保守のしやすさを考慮しています。


### フロントエンド | Frontend
- [React](https://reactjs.org/) + [TypeScript](https://www.typescriptlang.org/)
- [Zustand](https://github.com/pmndrs/zustand) (状態管理 | State management)
- [React Query](https://tanstack.com/query/latest) (データフェッチ | Data fetching)
- [shadcn/ui](https://ui.shadcn.com/) + [Tailwind CSS](https://tailwindcss.com/) (UI)
- [Vite](https://vitejs.dev/) (ビルドツール | Build tool)

### バックエンド | Backend
- [Express.js](https://expressjs.com/) + [TypeScript](https://www.typescriptlang.org/)
- [PostgreSQL](https://www.postgresql.org/) + [Prisma ORM](https://www.prisma.io/)
- [JWT](https://jwt.io/) 認証 | Authentication
- [Zod](https://zod.dev/) (バリデーション | Validation)

## 開発環境のセットアップ | Development Setup

ローカル環境では、バックエンドとフロントエンドを個別に起動する方法に加え、Docker Compose を利用したセットアップにも対応しています。初期構築後は環境変数、データベースマイグレーション、API / フロントエンドの起動状態を確認してください。


### 前提条件 | Prerequisites
- Node.js (v18.x 以上 | or higher)
- PostgreSQL (v14.x 以上 | or higher)
- Docker (オプション | optional)

### 手動セットアップ | Manual Setup

1. リポジトリのクローン | Clone the repository
```bash
git clone https://github.com/username/attendance-system.git
cd attendance-system
```

2. バックエンドのセットアップ | Backend setup
```bash
cd backend
npm install
cp .env.example .env  # 環境変数を設定 | Configure environment variables
npx prisma migrate dev
npm run dev
```

3. フロントエンドのセットアップ | Frontend setup
```bash
cd frontend
npm install
cp .env.example .env  # 環境変数を設定 | Configure environment variables
npm run dev
```

### Dockerを使用したセットアップ | Docker Setup

Docker Composeを使用して簡単にアプリケーションを起動できます：

```bash
docker-compose up -d
```

詳細なDockerセットアップ手順は [docs/docker-setup.md](docs/docker-setup.md) を参照してください。

*For detailed Docker setup instructions, refer to [docs/docker-setup.md](docs/docker-setup.md).*

## 使用方法 | Usage

起動後は、従業員・管理者の権限に応じて利用できる機能が切り替わります。開発環境では以下のURLからフロントエンド、バックエンドAPI、およびAPIドキュメントへアクセスできます。


1. ブラウザで以下のURLにアクセス | Access the following URLs in your browser:
   - フロントエンド | Frontend: http://localhost:3000
   - バックエンドAPI | Backend API: http://localhost:5000

2. デフォルトの管理者アカウントでログイン | Login with default admin account:
   - メール | Email: admin@example.com
   - パスワード | Password: password

### API ドキュメント | API Documentation

API の詳細なドキュメントは以下で確認できます | Detailed API documentation can be found at:
- 開発環境 | Development: http://localhost:5000/api-docs
- 本番環境 | Production: https://api.attendance-system.example.com/api-docs

## プロジェクト構造 | Project Structure

フロントエンドとバックエンドを分離し、バックエンドでは controllers / services / routes / middlewares、フロントエンドでは components / pages / hooks / store / services など、責務ごとにコードを整理しています。これにより、機能追加や変更の影響範囲を把握しやすくしています。


```
attendance-system/
├── backend/                # バックエンドアプリケーション | Backend application
│   ├── src/
│   │   ├── controllers/    # リクエストハンドラ | Request handlers
│   │   ├── middlewares/    # ミドルウェア | Middlewares
│   │   ├── routes/         # APIルート定義 | API route definitions
│   │   ├── services/       # ビジネスロジック | Business logic
│   │   ├── utils/          # ユーティリティ関数 | Utility functions
│   │   ├── app.ts          # Express アプリケーション | Express application
│   │   └── server.ts       # サーバー起動ファイル | Server startup file
│   ├── prisma/             # Prisma スキーマと移行 | Prisma schema and migrations
│   └── tests/              # テストファイル | Test files
│
├── frontend/               # フロントエンドアプリケーション | Frontend application
│   ├── src/
│   │   ├── components/     # Reactコンポーネント | React components
│   │   ├── hooks/          # カスタムフック | Custom hooks
│   │   ├── pages/          # ページコンポーネント | Page components
│   │   ├── store/          # Zustand ストア | Zustand stores
│   │   ├── services/       # API通信関連 | API communication
│   │   └── types/          # TypeScript型定義 | TypeScript type definitions
│   └── tests/              # テストファイル | Test files
│
├── docs/                   # ドキュメント | Documentation
└── docker-compose.yml      # Docker Compose 設定 | Docker Compose configuration
```

## テスト | Testing

バックエンド・フロントエンドのテストに加え、E2Eテストを実行できる構成を用意しています。新しい機能を追加する際には、既存機能への影響を確認しながらテストを追加・更新することを推奨します。


### バックエンドテスト | Backend Tests

```bash
cd backend
# すべてのシンプルテストを実行 | Run all simple tests
npm run test:all

# Jest テストを実行 (開発中) | Run Jest tests (in development)
npm test
```

詳細なテスト情報は [backend/tests/README.md](backend/tests/README.md) を参照してください。
*For detailed testing information, refer to [backend/tests/README.md](backend/tests/README.md).*

### フロントエンドテスト | Frontend Tests

```bash
cd frontend
npm test
```

### E2Eテスト | E2E Tests

```bash
npm run test:e2e
```

## 📌 開発・運用上の補足 | Notes

- `.env` などの環境依存設定はリポジトリへ直接コミットせず、`.env.example` を基準に設定してください。
- 本番環境では、デフォルト認証情報を必ず変更し、適切なシークレット管理を行ってください。
- API・データベースへのアクセスは、利用環境に応じて認証・認可・ネットワーク制御を適切に設定してください。
- 勤怠データは業務上重要な情報となるため、バックアップ、ログ管理、アクセス権限などの運用設計を環境に合わせて実施してください。

## ライセンス | License

このプロジェクトは MIT ライセンスの下で公開されています。詳細は [LICENSE](LICENSE) ファイルを参照してください。
*This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.*
