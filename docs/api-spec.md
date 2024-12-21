# API Specification

## Endpoints

### Rounds

#### GET /api/rounds/current
Get current active round
```typescript
Response {
  roundId: string
  question: string
  personality: {
    type: string
    traits: string[]
  }
  endTime: number
  totalStaked: string
}
```

#### POST /api/rounds/:roundId/answers
Submit answer for round
```typescript
Request {
  answer: string
  team: 'yes' | 'no'
  walletAddress: string
}

Response {
  success: boolean
  transactionHash?: string
}
```

### Wallet

#### POST /api/wallet/connect
Connect or create wallet via Crossmint
```typescript
Request {
  email?: string
}

Response {
  walletAddress: string
  connected: boolean
}
```

### Evaluation

#### GET /api/rounds/:roundId/result
Get round results
```typescript
Response {
  roundId: string
  winningTeam: 'yes' | 'no'
  totalPrize: string
  reasoning: string
}
```
