# 🪙 COINSENSEI

**Pakistan's Premier P2P Crypto Exchange Platform**

A full-featured peer-to-peer cryptocurrency exchange platform built for the Pakistani market, enabling seamless USDT trading with instant PKR settlements through multiple payment methods.

[![Next.js](https://img.shields.io/badge/Next.js-15.3-black)](https://nextjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.8-blue)](https://www.typescriptlang.org/)
[![Supabase](https://img.shields.io/badge/Supabase-PostgreSQL-green)](https://supabase.com/)
[![License](https://img.shields.io/badge/License-Proprietary-red)](LICENSE.txt)

---

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Architecture](#architecture)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [Environment Variables](#environment-variables)
- [Database Setup](#database-setup)
- [Running the Application](#running-the-application)
- [Worker System](#worker-system)
- [API Documentation](#api-documentation)
- [Security Features](#security-features)
- [Deployment](#deployment)
- [Contributing](#contributing)
- [License](#license)

---

## 🎯 Overview

COINSENSEI is a comprehensive P2P cryptocurrency exchange platform designed specifically for the Pakistani market. It enables users to trade USDT (TRC20) with instant PKR settlements through popular payment methods including JazzCash, EasyPaisa, Bank Transfer, and Raast.

### Key Highlights

- ✅ **P2P Marketplace**: Direct peer-to-peer trading with escrow protection
- ✅ **Multiple Payment Methods**: JazzCash, EasyPaisa, Bank Transfer, Raast
- ✅ **Real-time Trading**: Live order book with WebSocket updates
- ✅ **KYC Verification**: Face recognition and identity verification
- ✅ **Advanced Security**: 2FA, MFA, encryption, cold storage
- ✅ **Admin Dashboard**: Comprehensive management interface
- ✅ **Worker System**: Automated deposit/withdrawal processing
- ✅ **Blockchain Integration**: TRON network (USDT-TRC20)

---

## ✨ Features

### User Features

- 🔐 **Secure Authentication**: Email/SMS OTP, 2FA, MFA support
- 👤 **KYC Verification**: Face recognition and document verification
- 💰 **Wallet Management**: PKR and USDT wallet support
- 📊 **Trading Interface**: Real-time order book and trade execution
- 💳 **Payment Integration**: Multiple Pakistani payment methods
- 📱 **Responsive Design**: Mobile-first, modern UI/UX
- 🔔 **Real-time Notifications**: WebSocket-based updates

### Admin Features

- 📈 **Dashboard**: Real-time system monitoring and metrics
- 👥 **User Management**: User overview, KYC reviews, verification
- 💵 **Financial Operations**: Deposit/withdrawal management
- 👛 **Wallet Management**: PKR and USDT wallet controls
- 🔄 **Worker Management**: Job queue monitoring and control
- 📋 **Transaction Logs**: Complete audit trail
- ⚙️ **System Configuration**: Platform settings and controls

### Technical Features

- 🚀 **High Performance**: Concurrent processing, batch operations
- 🔒 **Database Safety**: Atomic transactions, race condition protection
- 📊 **Monitoring**: Health checks, metrics, error tracking
- 🔄 **Auto Retry**: Exponential backoff for failed operations
- 🐳 **Docker Support**: Containerized deployment
- 📈 **Scalable Architecture**: Worker-based job processing

---

## 🛠️ Tech Stack

### Frontend

- **Framework**: Next.js 15.3 (App Router)
- **Language**: TypeScript 5.8
- **UI Library**: React 19
- **Styling**: Tailwind CSS 4
- **Components**: Radix UI, Headless UI
- **Animations**: Framer Motion
- **Charts**: Chart.js, Recharts
- **State Management**: TanStack Query (React Query)

### Backend

- **Runtime**: Node.js
- **API**: Next.js API Routes
- **Database**: Supabase (PostgreSQL)
- **Authentication**: Supabase Auth
- **Job Queue**: BullMQ, pg-boss
- **Real-time**: Socket.io
- **Blockchain**: TronWeb (TRON network)

### Infrastructure

- **Database**: PostgreSQL (via Supabase)
- **Cache**: Redis (via BullMQ)
- **Storage**: Supabase Storage
- **Email**: Nodemailer
- **SMS**: Twilio
- **Face Recognition**: face-api.js

### Development Tools

- **Package Manager**: npm
- **Linting**: ESLint
- **Type Checking**: TypeScript
- **Process Manager**: PM2 (production)
- **Containerization**: Docker

---

## 🏗️ Architecture

### System Components

```
┌─────────────────────────────────────────────────────────┐
│                    Frontend (Next.js)                    │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  │
│  │   User App   │  │  Admin App   │  │  Landing     │  │
│  └──────────────┘  └──────────────┘  └──────────────┘  │
└─────────────────────────────────────────────────────────┘
                        │
                        ▼
┌─────────────────────────────────────────────────────────┐
│                  API Layer (Next.js)                     │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  │
│  │   Auth API   │  │  Trade API   │  │  Admin API   │  │
│  └──────────────┘  └──────────────┘  └──────────────┘  │
└─────────────────────────────────────────────────────────┘
                        │
        ┌───────────────┼───────────────┐
        ▼               ▼               ▼
┌──────────────┐  ┌──────────────┐  ┌──────────────┐
│  Supabase    │  │  Worker      │  │  Blockchain  │
│  (PostgreSQL)│  │  System      │  │  (TRON)      │
└──────────────┘  └──────────────┘  └──────────────┘
```

### Worker System

- **Deposit Listener**: Monitors blockchain for incoming deposits
- **Withdrawal Worker**: Processes USDT withdrawals
- **Sync Worker**: Synchronizes wallet balances
- **Consolidation Worker**: Combines wallet funds
- **Gas Topup Worker**: Adds TRX for transaction fees
- **Cron Jobs**: Scheduled tasks for maintenance

---

## 🚀 Getting Started

### Prerequisites

- Node.js 18+ and npm
- PostgreSQL database (or Supabase account)
- Redis (for job queue)
- TRON network access (TronGrid API or full node)

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd Coinsensei
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up environment variables**
   ```bash
   cp .env.example .env.local
   # Edit .env.local with your configuration
   ```

4. **Set up the database**
   ```bash
   # Run database migrations (see Database Setup section)
   ```

5. **Start the development server**
   ```bash
   npm run dev
   ```

6. **Start workers (in separate terminals)**
   ```bash
   # Start all workers
   npm run system:start

   # Or start individually
   npm run worker:new-sync-balances
   npm run worker:new-gas-topup
   npm run worker:new-consolidation
   npm run listen:deposits
   npm run worker:withdrawal
   ```

---

## 📁 Project Structure

```
Coinsensei/
├── src/
│   ├── app/                    # Next.js app directory
│   │   ├── admin/              # Admin dashboard pages
│   │   ├── api/                # API routes
│   │   ├── auth/               # Authentication pages
│   │   └── user/               # User dashboard pages
│   ├── components/             # React components
│   ├── hooks/                  # Custom React hooks
│   ├── lib/                    # Utility libraries
│   ├── services/               # Business logic services
│   ├── types/                  # TypeScript type definitions
│   ├── websockets/             # WebSocket handlers
│   └── worker/                 # Worker scripts
├── workers/                    # Worker implementations
├── cron/                       # Cron job scripts
├── sql/                        # Database migration scripts
├── supabase/
│   └── migrations/             # Supabase migrations
├── docs/                       # Documentation
├── public/                     # Static assets
├── scripts/                    # Utility scripts
└── config/                     # Configuration files
```

---

## 🔐 Environment Variables

Create a `.env.local` file in the root directory:

```env
# Supabase Configuration
NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_anon_key
SUPABASE_SERVICE_ROLE_KEY=your_service_role_key

# Database
DATABASE_URL=your_postgres_connection_string

# Redis (for job queue)
REDIS_URL=redis://localhost:6379

# TRON Network
TRON_FULL_HOST=https://api.trongrid.io
TRON_TRC20_CONTRACT=TR7NHqjeKQxGTCi8q8ZY4pL8otSzgjLj6t

# Authentication
NEXTAUTH_SECRET=your_nextauth_secret
NEXTAUTH_URL=http://localhost:3000

# Email (Nodemailer)
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=your_email@gmail.com
SMTP_PASS=your_app_password

# SMS (Twilio)
TWILIO_ACCOUNT_SID=your_twilio_sid
TWILIO_AUTH_TOKEN=your_twilio_token
TWILIO_PHONE_NUMBER=your_twilio_number

# Application
NODE_ENV=development
NEXT_PUBLIC_APP_URL=http://localhost:3000

# Worker Configuration
POLL_INTERVAL=30000
BATCH_SIZE=50
CONCURRENCY_LIMIT=5
REQUEST_TIMEOUT=10000
MAX_RETRIES=3
```

---

## 🗄️ Database Setup

### Initial Setup

1. **Create Supabase project** or set up PostgreSQL database

2. **Run database migrations** (in order):
   ```sql
   -- 1. System configuration
   \i sql/create_system_config_table.sql
   
   -- 2. Admin actions logging
   \i sql/create_admin_actions_table.sql
   
   -- 3. Job queue system
   \i sql/create_job_logs_table.sql
   
   -- 4. Worker system columns
   \i sql/add_worker_system_columns.sql
   
   -- 5. Foreign key relationships
   \i sql/create_foreign_key_relationships.sql
   
   -- 6. Other required tables
   \i sql/create_withdrawal_jobs_table.sql
   \i sql/create_user_security_table.sql
   \i sql/create_security_audit_table.sql
   ```

3. **Set up Row Level Security (RLS)** policies in Supabase

4. **Configure database functions** for deposit processing

See `docs/worker-system-setup.md` for detailed database setup instructions.

---

## 🏃 Running the Application

### Development Mode

```bash
# Start Next.js development server
npm run dev

# Start WebSocket server (in separate terminal)
npm run dev:socket

# Start workers (in separate terminals)
npm run system:start
```

### Production Mode

```bash
# Build the application
npm run build

# Start production server
npm start

# Start workers with PM2
pm2 start ecosystem.config.js
```

### Individual Services

```bash
# Workers
npm run worker:new-sync-balances      # Balance sync worker
npm run worker:new-gas-topup         # Gas topup worker
npm run worker:new-consolidation     # Consolidation worker
npm run listen:deposits              # Deposit listener
npm run worker:withdrawal            # Withdrawal worker

# Cron jobs
npm run cron:balance-sync            # Scheduled balance sync
npm run cron:cleanup                 # Cleanup stuck jobs
npm run cron:queue-jobs              # Queue dependent jobs
```

---

## ⚙️ Worker System

The platform uses a distributed worker system for processing various background tasks:

### Worker Types

1. **Deposit Listener** (`listen:deposits`)
   - Monitors TRON blockchain for incoming USDT deposits
   - Processes deposits with atomic transactions
   - Concurrent processing with rate limiting

2. **Sync Worker** (`worker:new-sync-balances`)
   - Synchronizes wallet balances with blockchain
   - Updates transaction history
   - Handles balance discrepancies

3. **Consolidation Worker** (`worker:new-consolidation`)
   - Combines funds from multiple wallets
   - Optimizes wallet structure
   - Reduces transaction fees

4. **Gas Topup Worker** (`worker:new-gas-topup`)
   - Adds TRX to wallets for transaction fees
   - Ensures sufficient gas for operations
   - Monitors gas levels

5. **Withdrawal Worker** (`worker:withdrawal`)
   - Processes USDT withdrawal requests
   - Handles on-chain transactions
   - Manages withdrawal queue

### Worker Management

Access the admin worker dashboard at `/admin/workers` to:
- Monitor worker status and performance
- Queue jobs manually
- Control worker lifecycle
- View job statistics
- Handle errors and retries

See `docs/worker-system-setup.md` for detailed documentation.

---

## 📡 API Documentation

### Authentication Endpoints

- `POST /api/auth/login` - User login
- `POST /api/auth/signup` - User registration
- `POST /api/auth/logout` - User logout
- `POST /api/password-reset/check-user` - Password reset

### Security Endpoints

- `POST /api/security/enable-2fa` - Enable 2FA
- `POST /api/security/verify-2fa` - Verify 2FA
- `POST /api/mfa` - Multi-factor authentication
- `POST /api/send-email-otp` - Send email OTP
- `POST /api/verify-email-otp` - Verify email OTP

### KYC Endpoints

- `POST /api/kyc-submit` - Submit KYC documents
- `POST /api/face-check` - Face recognition verification

### Admin Endpoints

- `GET /api/admin/users` - Get all users
- `POST /api/admin/dispatch-job` - Dispatch worker job
- `POST /api/admin/workers/control` - Control worker system
- `GET /api/workers/stats` - Get worker statistics

### Trading Endpoints

- `GET /api/trades` - Get trade history
- `POST /api/trades/create` - Create trade order
- `GET /api/orderbook` - Get order book

---

## 🔒 Security Features

### Authentication & Authorization

- ✅ Email/SMS OTP verification
- ✅ Two-Factor Authentication (2FA)
- ✅ Multi-Factor Authentication (MFA)
- ✅ Session management with Supabase Auth
- ✅ Role-based access control (RBAC)
- ✅ Admin-only endpoints protection

### Data Protection

- ✅ 256-bit encryption for sensitive data
- ✅ SQL injection prevention
- ✅ XSS protection
- ✅ CSRF tokens
- ✅ Rate limiting on API endpoints
- ✅ Input validation and sanitization

### Blockchain Security

- ✅ Cold storage for majority of funds
- ✅ Multi-signature wallet support
- ✅ Transaction verification
- ✅ Atomic transaction processing
- ✅ Duplicate transaction prevention

### Monitoring & Auditing

- ✅ Security audit logs
- ✅ Admin action tracking
- ✅ Failed login attempt monitoring
- ✅ Transaction history logging
- ✅ Real-time security alerts

---

## 🚢 Deployment

### Docker Deployment

```bash
# Build Docker image
docker build -t coinsensei:latest .

# Run container
docker run -d \
  --name coinsensei \
  --env-file .env.local \
  -p 3000:3000 \
  coinsensei:latest
```

### PM2 Deployment

```bash
# Install PM2 globally
npm install -g pm2

# Start application
pm2 start npm --name "coinsensei" -- start

# Start workers
pm2 start ecosystem.config.js

# Save PM2 configuration
pm2 save
pm2 startup
```

### Environment-Specific Configuration

- **Development**: Use `.env.local`
- **Staging**: Use `.env.staging`
- **Production**: Use `.env.production`

### Health Checks

- Application: `GET /api/health`
- Deposit Listener: `GET http://localhost:3001/health`
- Workers: Check via admin dashboard

---

## 📚 Documentation

Additional documentation is available in the `docs/` directory:

- [`worker-system-setup.md`](docs/worker-system-setup.md) - Worker system setup guide
- [`deposit-listener-improvements.md`](docs/deposit-listener-improvements.md) - Deposit listener documentation
- [`admin-dashboard-enhancement-summary.md`](docs/admin-dashboard-enhancement-summary.md) - Admin dashboard features
- [`admin-usdt-withdrawals-phase1.md`](docs/admin-usdt-withdrawals-phase1.md) - Withdrawal management guide

---

## 🤝 Contributing

This is a private project. For contributions, please contact the project maintainers.

### Development Guidelines

1. Follow TypeScript best practices
2. Use ESLint for code quality
3. Write descriptive commit messages
4. Test changes thoroughly
5. Update documentation as needed

---

## 📄 License

This project is proprietary and confidential. See [LICENSE.txt](LICENSE.txt) for details.

---

## 📞 Support

For support and inquiries:
- **Email**: support@coinsensei.com
- **Documentation**: See `docs/` directory
- **Issues**: Contact project maintainers

---

## 🎉 Acknowledgments

Built with:
- [Next.js](https://nextjs.org/)
- [Supabase](https://supabase.com/)
- [TronWeb](https://www.tronweb.org/)
- [Tailwind CSS](https://tailwindcss.com/)
- And many other open-source libraries

---

**Made with ❤️ for Pakistan's crypto community**

