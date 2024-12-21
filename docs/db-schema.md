# Database Schema

## SQLite Tables

### rounds
```sql
CREATE TABLE rounds (
    id INTEGER PRIMARY KEY,
    question TEXT NOT NULL,
    personality_type TEXT NOT NULL,
    start_time INTEGER NOT NULL,
    end_time INTEGER NOT NULL,
    status TEXT NOT NULL,
    winning_team TEXT,
    contract_address TEXT NOT NULL,
    transaction_hash TEXT NOT NULL
);
```

### answers
```sql
CREATE TABLE answers (
    id INTEGER PRIMARY KEY,
    round_id INTEGER NOT NULL,
    wallet_address TEXT NOT NULL,
    team TEXT NOT NULL,
    message TEXT NOT NULL,
    timestamp INTEGER NOT NULL,
    transaction_hash TEXT NOT NULL,
    FOREIGN KEY (round_id) REFERENCES rounds (id)
);
```

### evaluations
```sql
CREATE TABLE evaluations (
    id INTEGER PRIMARY KEY,
    round_id INTEGER NOT NULL,
    result TEXT NOT NULL,
    reasoning TEXT NOT NULL,
    timestamp INTEGER NOT NULL,
    transaction_hash TEXT NOT NULL,
    FOREIGN KEY (round_id) REFERENCES rounds (id)
);
``` 