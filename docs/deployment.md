# Hackathon MVP (4 Days)

## Day 1: Foundation & Smart Contract
- [x] **Project Setup**
  - Initialize monorepo with pnpm
  - Configure SQLite
  - Basic Express server
  - ✓ Checkpoint: `pnpm dev` runs successfully

- [x] **Smart Contract Development**
  - RoundManager.sol implementation
    - Round creation
    - Bet placement
    - Round completion
  - Deploy to Mode testnet
  - Basic contract testing
  - ✓ Checkpoint: Contract deployed & verified

**Day 1 Fallback Plan**:
- If Mode testnet issues: Use local hardhat network
- If pnpm issues: Use separate repos temporarily

## Day 2: Core Integrations (Critical Day)
- [ ] **Morning: Eliza + GOAT Setup**
  - Basic Eliza configuration
  - GOAT SDK integration
  - Test round initialization
  - ✓ Checkpoint: Eliza can trigger contract via GOAT

- [ ] **Afternoon: Crossmint Integration**
  - Wallet creation flow
  - Basic payment processing
  - ✓ Checkpoint: Can create wallet & process test payment

- [ ] **Evening: Integration Testing**
  - Test complete flow:
    ```
    Eliza -> GOAT -> Mode
    Crossmint -> GOAT -> Mode
    ```
  - ✓ Checkpoint: All core integrations working

**Day 2 Fallback Plans**:
- Eliza issues: Use simplified evaluation logic
- GOAT issues: Direct contract interaction
- Crossmint issues: Use basic wallet connection

## Day 3: Backend & Frontend Base
- [ ] **Backend Implementation**
  - Round management API
  - Answer submission endpoints
  - SQLite integration
  - ✓ Checkpoint: APIs working with Postman

- [ ] **Frontend Foundation**
  - React project setup
  - Current round display
  - Wallet connection
  - Basic betting UI
  - ✓ Checkpoint: Can connect wallet & view round

**Day 3 Fallback Plan**:
- If time issues: Simplify UI, focus on functionality

## Day 4: Integration & Polish
- [ ] **Morning: Flow Completion**
  - Complete User Onboarding flow
  - Complete Round Management flow
  - Complete User Participation flow
  - ✓ Checkpoint: All flows working

- [ ] **Afternoon: Testing**
  - End-to-end testing
  - Fix critical issues
  - ✓ Checkpoint: Core flows stable

- [ ] **Evening: Demo Prep**
  - Prepare script
  - Record video
  - ✓ Checkpoint: Demo ready

**Day 4 Fallback Plan**:
- Focus on one perfect flow if time runs short

## Critical Paths to Test

### 1. Round Management (Priority 1)
```mermaid
Timer -> Eliza -> SQLite -> GOAT -> Mode
```
- Must work: Round creation & management
- Should work: Question generation
- Nice to have: Advanced evaluation

### 2. User Participation (Priority 1)
```mermaid
User -> Frontend -> Crossmint -> GOAT -> Mode
```
- Must work: Team selection & bet placement
- Should work: Wallet creation
- Nice to have: Transaction history

### 3. Evaluation (Priority 2)
```mermaid
Timer -> Eliza -> GOAT -> Mode -> Crossmint
```
- Must work: Basic winner selection by team
- Should work: Reward distribution to winning team
- Nice to have: Detailed evaluation

## Success Criteria
- [ ] Users can connect wallet
- [ ] Users can select teams
- [ ] Users can place bets
- [ ] Users can submit answers
- [ ] System can evaluate winning team
- [ ] Rewards can be distributed to winning team

## Emergency Simplifications (if needed)
1. Remove complex evaluations
2. Simplify betting mechanism
3. Basic UI without animations
4. Manual round initialization
