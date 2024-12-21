# Technical Specification

## 1. Core Components

### 1.1 Eliza Integration
```typescript
import { ElizaRuntime } from '@ai16z/eliza';

const oracle = new ElizaRuntime({
  personality: {
    type: 'witty_judge',
    traits: ['sarcastic', 'funny'],
    evaluationCriteria: ['creativity', 'humor']
  }
});

// Core evaluation logic
async function evaluateAnswers(answers: Answer[]) {
  return oracle.evaluate(answers, {
    criteria: ['humor', 'creativity'],
    teamBased: true
  });
}
```

### 1.2 GOAT Integration
```typescript
import { getOnChainTools } from '@goat-sdk/core';

const tools = getOnChainTools({
  mode: {
    network: MODE_TESTNET,
    contracts: {
      roundManager: ROUND_MANAGER_ADDRESS
    }
  }
});

// Core blockchain operations
async function handleRoundOperations() {
  // Initialize round
  const tx = await tools.initializeRound({
    duration: ROUND_DURATION,
    minStake: MIN_STAKE_AMOUNT
  });

  // Process bets
  await tools.placeBet(roundId, amount);

  // Complete round
  await tools.completeRound(roundId, winningTeam);
}
```

### 1.3 Crossmint Integration
```typescript
import { CrossmintClient } from '@crossmint/client-sdk';

const client = new CrossmintClient({
  projectId: CROSSMINT_PROJECT_ID
});

// Wallet operations
async function handleWallet() {
  const wallet = await client.createWallet();
  await client.processPayment(amount);
}
```

## 2. Core Processes

### 2.1 Round Management
- Timer-based round initialization
- Question generation via Eliza
- On-chain round creation via GOAT
- State synchronization with SQLite

### 2.2 User Participation
- Wallet connection via Crossmint
- Bet processing through GOAT
- Answer storage in SQLite
- Transaction confirmation flow

### 2.3 Evaluation Process
- Answer collection from SQLite
- Evaluation via Eliza
- Result submission through GOAT
- Reward distribution via Crossmint

## 3. Data Models

### 3.1 Round
```typescript
interface Round {
  id: string;
  question: string;
  status: 'active' | 'evaluating' | 'completed';
  startTime: number;
  endTime: number;
  contractAddress: string;
}
```

### 3.2 Answer
```typescript
interface Answer {
  roundId: string;
  walletAddress: string;
  team: 'yes' | 'no';
  message: string;
  transactionHash: string;
}
```

### 3.3 Evaluation
```typescript
interface Evaluation {
  roundId: string;
  result: 'yes' | 'no';
  reasoning: string;
  transactionHash: string;
}
```

## 4. Error Handling

### 4.1 Transaction Failures
```typescript
async function handleTransaction(operation: () => Promise<any>) {
  try {
    return await operation();
  } catch (error) {
    if (error.code === 'NETWORK_ERROR') {
      return await retryOperation(operation);
    }
    throw error;
  }
}
```

### 4.2 State Recovery
```typescript
async function syncState(roundId: string) {
  const chainState = await tools.getRoundState(roundId);
  const dbState = await db.getRound(roundId);
  
  if (chainState.status !== dbState.status) {
    await db.updateRound(roundId, chainState);
  }
}
```
