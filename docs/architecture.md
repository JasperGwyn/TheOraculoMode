# System Architecture

## Overview
A decentralized debate platform where an AI agent (Eliza) evaluates whimsical debates, managing rewards through Mode Network and providing seamless user experience via Crossmint.

## Core Components

### 1. AI Core (Eliza)
- **Responsibilities**:
  - Question generation
  - Answer evaluation
  - Winner determination
- **Key Features**:
  - Single personality configuration
  - Team-based evaluation
  - Autonomous operation

### 2. Blockchain Layer
- **Mode Network**:
  - Round state management
  - Stake handling
  - Reward distribution
- **GOAT SDK**:
  - Transaction management
  - Contract interaction
  - Event handling
- **Crossmint**:
  - Wallet creation/management
  - Payment processing
  - Transaction simplification

### 3. Data Management
- **Off-Chain (SQLite)**:
  - Round details
  - User answers
  - Evaluation results
- **On-Chain (Mode)**:
  - Active rounds
  - Stakes and bets
  - Winner records

### 4. Frontend
- **React Application**:
  - Round display
  - Answer submission
  - Wallet integration
  - Result visualization

## System Interactions

### 1. Core Flows
- Round Management
- User Participation
- Evaluation Process
- Reward Distribution

### 2. Data Flow
- Frontend ↔ Backend ↔ SQLite
- Frontend ↔ Crossmint ↔ Mode
- Eliza ↔ GOAT ↔ Mode

### 3. State Management
- SQLite for application state
- Mode Network for financial state
- GOAT for state synchronization

## Technical Decisions

### 1. Storage Strategy
- SQLite for speed and simplicity
- Mode Network for critical data
- Hybrid approach for optimal performance

### 2. Integration Approach
- GOAT SDK for blockchain operations
- Crossmint for user onboarding
- Direct Eliza integration

### 3. Security Model
- Smart contract authorization
- Transaction validation
- State verification

## Development Considerations

### 1. Scalability
- SQLite limitations
- Mode Network throughput
- Evaluation processing

### 2. Reliability
- Transaction retry mechanism
- State recovery procedures
- Error handling strategy

### 3. Maintainability
- Modular components
- Clear interfaces
- Simple deployment