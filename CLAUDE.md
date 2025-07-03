# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

RepoScore is a web application that analyzes GitHub repository commits using AI-powered quality and impact scoring. The system evaluates individual commits on both quality (0-3 scale) and impact (-2 to +6 scale) dimensions, providing insights into developer productivity and code contribution patterns.

## Core Architecture

### Technology Stack
- **Frontend**: Next.js 15 with React 19, TypeScript, Tailwind CSS
- **Backend**: Next.js API routes with Server-Side Rendering
- **Database**: Supabase (PostgreSQL)
- **AI Analysis**: OpenAI GPT-4 for commit evaluation
- **Version Control Integration**: GitHub API with Personal Access Tokens

### Key Components

**Database Schema** (see `supabase/migrations/001_initial_schema.sql`):
- `users` - User authentication and profiles
- `repositories` - Connected GitHub repositories with PAT tokens
- `commits` - Individual commit analysis with AI scores
- `analysis_authors` - Aggregated developer metrics
- `evaluation_history` - Audit trail for manual score edits

**API Layer** (`src/app/api/`):
- Authentication endpoints (`/auth/*`) using JWT tokens
- Repository management (`/repositories/*`) 
- Commit analysis orchestration (`/analyze/`) with streaming status
- Results retrieval and updates (`/commits/*`)

**Analysis Engine** (`src/app/api/analyze/route.ts`):
- Fetches commits from GitHub API in date ranges
- Processes commits in batches of 5 to manage rate limits
- Dual AI evaluation: Impact scoring and Quality scoring
- Stores results with language detection and flagging

**AI Prompts** (`src/lib/openai.ts`):
- **Impact Prompt**: Evaluates commits on business/technical impact (-2 to +6)
- **Quality Prompt**: Analyzes code quality, style, and maintainability (0-3)
- Both prompts enforce strict JSON output format with error handling

## Development Commands

```bash
# Install dependencies
npm install

# Development server with Turbopack
npm run dev

# Production build
npm run build

# Production server
npm start

# Linting
npm run lint
```

## Environment Setup

Required environment variables:
- `NEXT_PUBLIC_SUPABASE_URL` - Supabase project URL
- `NEXT_PUBLIC_SUPABASE_ANON_KEY` - Supabase anonymous key
- `SUPABASE_SERVICE_ROLE_KEY` - Supabase service role key
- `OPENAI_API_KEY` - OpenAI API key for GPT-4 analysis
- `NEXTAUTH_SECRET` - JWT signing secret
- `NEXTAUTH_URL` - Application URL
- `GITHUB_TOKEN` - Optional GitHub PAT for higher rate limits

## Key Implementation Details

### Commit Analysis Flow
1. User connects GitHub repository with PAT token
2. Analysis triggered via `/api/analyze` endpoint
3. System fetches commits using GitHub API with date filtering
4. Each commit analyzed by two separate GPT-4 calls (impact + quality)
5. Results parsed from JSON responses with fallback error handling
6. Commit data stored with language detection and aggregation

### Authentication System
- JWT-based authentication with HTTP-only cookies
- User sessions managed through middleware
- Repository access controlled by user ownership

### Rate Limiting Strategy
- Batch processing (5 commits per batch)
- 1-second delays between batches
- GitHub PAT tokens for higher API limits
- Analysis status tracking with progress updates

## Working Directory Structure

The main application code is in `repo-score-web/` subdirectory. Always ensure you're working in the correct path when running commands or editing files.

## Database Operations

Use Supabase client (`src/lib/supabase.ts`) for all database operations. The application uses row-level security policies, so ensure proper user context in queries.

## AI Analysis Guidelines

Both impact and quality prompts are designed to return structured JSON. The system includes robust error handling for parsing failures with meaningful fallbacks. When modifying prompts, maintain the strict JSON requirement and scoring ranges.

## Language
Speak in spanish when possible.