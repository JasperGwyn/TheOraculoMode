# Development Notes

## Simplified Structure
```
oracle/
├── packages/
│   ├── contracts/
│   │   └── src/
│   │       └── RoundManager.sol    # Single contract
│   ├── backend/
│   │   └── src/
│   │       ├── index.ts           # Main server
│   │       ├── eliza.ts          # Simple Eliza setup
│   │       └── db.ts            # Basic SQLite
│   └── frontend/
│       └── src/
│           ├── App.tsx          # Main app
│           └── components/      # Basic components
```

## Workspace Setup
```yaml:pnpm-workspace.yaml
packages:
  - 'packages/*'
```

```json:package.json
{
  "name": "oracle",
  "private": true,
  "scripts": {
    "dev": "pnpm -r dev",
    "build": "pnpm -r build",
    "test": "pnpm -r test"
  }
}
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
1. Install pnpm (if not installed):
   ```powershell
   # Using PowerShell
   iwr https://get.pnpm.io/install.ps1 -useb | iex
   ```

2. Install dependencies:
   ```powershell
   # Install all workspace dependencies
   pnpm install
   ```

3. Setup local environment:
   ```powershell
   # Copy environment templates
   Copy-Item .env.example -Destination .env
   
   # Initialize SQLite database
   pnpm --filter backend db:init
   ```

4. Start development servers:
   ```powershell
   # Start all services
   pnpm dev

   # Or start individual services in separate terminals
   pnpm --filter backend dev
   pnpm --filter frontend dev
   ```

## Testing
```powershell
# Run all tests
pnpm test

# Run specific package tests
pnpm --filter contracts test
pnpm --filter backend test
pnpm --filter frontend test
```

## Common Commands
```powershell
# Add dependency to specific package
pnpm --filter backend add express
pnpm --filter frontend add react

# Add development dependency
pnpm --filter contracts add -D hardhat

# Run specific script in package
pnpm --filter backend typecheck

# Environment variables in PowerShell
$env:MODE_NETWORK_URL = "your-url"
$env:CROSSMINT_API_KEY = "your-key"

# Or set them permanently
[System.Environment]::SetEnvironmentVariable('MODE_NETWORK_URL', 'your-url', 'User')
```

## Useful PowerShell Tips
```powershell
# Check node version
node --version

# Check pnpm version
pnpm --version

# Clear terminal
Clear-Host   # or cls

# Kill process on port
Stop-Process -Id (Get-NetTCPConnection -LocalPort 3000).OwningProcess -Force
```