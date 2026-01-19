# Contract Manager

A modern, elegant web application for storing and managing construction contracts across multiple projects. Built with React, TypeScript, and Supabase.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![React](https://img.shields.io/badge/React-18-61dafb.svg)
![TypeScript](https://img.shields.io/badge/TypeScript-5-3178c6.svg)
![Supabase](https://img.shields.io/badge/Supabase-Backend-3ecf8e.svg)

## Features

- **Multi-Project Support** — Organize contracts by construction project
- **Contract Management** — Full CRUD operations with status tracking
- **PDF Storage** — Upload and preview contract documents via Supabase Storage
- **Clean UI** — Minimal, modern interface with excellent UX
- **Secure** — Row Level Security ensures data isolation
- **Real-time Ready** — Built on Supabase for future real-time features

## Tech Stack

| Layer | Technology |
|-------|------------|
| Frontend | React 18 + TypeScript |
| Build | Vite |
| Routing | React Router v6 |
| Styling | Tailwind CSS |
| State | TanStack Query |
| Forms | React Hook Form + Zod |
| Backend | Supabase (PostgreSQL + Storage + Auth) |
| Icons | Lucide React |

## Getting Started

### Prerequisites

- Node.js 18+
- npm or yarn
- Supabase account (project already configured)

### Installation

```bash
# Clone the repository
git clone https://github.com/Shossy-lab/contract-manager.git
cd contract-manager

# Install dependencies
npm install

# Copy environment variables
cp .env.example .env.local

# Start development server
npm run dev
```

### Environment Variables

Create a `.env.local` file with:

```env
VITE_SUPABASE_URL=https://hmrsdovclzbzzsypbtod.supabase.co
VITE_SUPABASE_ANON_KEY=your_anon_key_here
```

## Database Schema

### Contracts Table

The `contracts` table stores all contract information:

| Column | Type | Description |
|--------|------|-------------|
| `id` | UUID | Primary key |
| `project_id` | UUID | Foreign key to projects |
| `name` | VARCHAR(255) | Contract name |
| `contractee` | VARCHAR(255) | Contractor/vendor name |
| `date_issued` | DATE | Issue date |
| `amount` | DECIMAL(12,2) | Contract value |
| `notes` | TEXT | Additional notes |
| `pdf_path` | TEXT | Storage path to PDF |
| `pdf_filename` | VARCHAR(255) | Original filename |
| `status` | VARCHAR(50) | draft/sent/signed/completed/cancelled |
| `created_at` | TIMESTAMPTZ | Creation timestamp |
| `updated_at` | TIMESTAMPTZ | Last update timestamp |
| `created_by` | UUID | User who created |

### Storage

PDF files are stored in the `contracts` bucket with the path structure:
```
contracts/{organization_id}/{project_id}/{contract_id}/{filename}.pdf
```

## Project Structure

```
src/
├── components/
│   ├── ui/              # Base UI components
│   ├── layout/          # App layout
│   ├── projects/        # Project components
│   ├── contracts/       # Contract components
│   └── dashboard/       # Dashboard widgets
├── pages/               # Route pages
├── hooks/               # Custom React hooks
├── lib/                 # Utilities & Supabase client
├── services/            # API service layer
├── types/               # TypeScript types
└── context/             # React context providers
```

## Available Scripts

```bash
npm run dev      # Start dev server
npm run build    # Production build
npm run preview  # Preview production build
npm run lint     # Run ESLint
npm run test     # Run tests
```

## Contract Status Workflow

```
Draft → Sent → Signed → Completed
                  ↓
              Cancelled
```

## License

MIT License — see [LICENSE](LICENSE) for details.

---

Built with precision for Szostak Build LLC
