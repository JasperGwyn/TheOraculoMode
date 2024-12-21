# Development Notes

## Project Structure
```
oracle/
├── contracts/               # Smart Contracts
│   ├── RoundManager.sol
│   └── PrizePool.sol
├── backend/                # Node.js + Express
│   ├── src/
│   │   ├── eliza/         # Eliza Agent
│   │   ├── db/           # SQLite management
│   │   ├── blockchain/   # GOAT + Mode integration
│   │   └── api/          # Express routes
│   └── tests/
├── frontend/              # React + TypeScript
│   ├── src/
│   │   ├── components/
│   │   ├── hooks/
│   │   ├── services/
│   │   └── pages/
│   └── tests/
└── scripts/              # Deployment & utilities
```

## Environment Variables
```env
# Backend
MODE_NETWORK_URL=
MODE_PRIVATE_KEY=
CROSSMINT_API_KEY=
CROSSMINT_PROJECT_ID=
SQLITE_PATH=

# Frontend
REACT_APP_BACKEND_URL=
REACT_APP_MODE_NETWORK=
REACT_APP_CROSSMINT_CLIENT_ID=
```

## Development Setup
1. Install dependencies:
   ```bash
   # Install contract dependencies
   cd contracts && npm install
   
   # Install backend dependencies
   cd backend && npm install
   
   # Install frontend dependencies
   cd frontend && npm install
   ```

2. Setup local environment:
   ```bash
   # Copy environment templates
   cp .env.example .env
   
   # Initialize SQLite database
   npm run db:init
   ```

3. Start development servers:
   ```bash
   # Terminal 1: Start backend
   cd backend && npm run dev
   
   # Terminal 2: Start frontend
   cd frontend && npm start
   ```

## Testing
```bash
# Run contract tests
cd contracts && npx hardhat test

# Run backend tests
cd backend && npm test

# Run frontend tests
cd frontend && npm test
```