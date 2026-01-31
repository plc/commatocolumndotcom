# CLAUDE.md

This file provides instructions for AI assistants (like Claude) working with this codebase.

## Project Overview

Comma to Column is a simple webapp that converts column data to SQL IN statements.

**Example:**
```
dog
cat
bird
```
becomes:
```sql
IN ('dog','cat','bird')
```

## Tech Stack

- Node.js with Express
- Docker for local development
- Fly.io for production deployment
- No database required (client-side only logic)

## Common Tasks

### Start Local Development Server

```bash
docker compose up --build
```

The server runs at http://127.0.0.1:3000

### Deploy to Fly.io

```bash
fly deploy
```

### Run Tests

```bash
npm test
```

## Project Structure

```
src/index.js        - Express server with single-page app
src/healthcheck.js  - Health check script
Dockerfile          - Production container
docker-compose.yml  - Local development
fly.toml            - Fly.io configuration
```

## Key Files

- **src/index.js** - Contains the Express server and the full HTML/CSS/JS for the webapp
- **package.json** - Dependencies (just Express)

## Environment Variables

| Variable | Description |
|----------|-------------|
| `PORT` | Server port (default: 3000) |
