# Smart Contracts

## RoundManager.sol
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.19;

contract RoundManager {
    enum RoundStatus { Active, Evaluating, Completed }
    enum Team { None, Yes, No }

    struct Round {
        uint256 id;
        RoundStatus status;
        uint256 startTime;
        uint256 endTime;
        uint256 totalStaked;
        mapping(Team => uint256) teamStakes;
        Team winningTeam;
    }

    mapping(uint256 => Round) public rounds;
    mapping(address => bool) public authorizedProcessors;

    event RoundCreated(uint256 roundId, uint256 startTime);
    event BetPlaced(uint256 roundId, address user, Team team, uint256 amount);
    event RoundCompleted(uint256 roundId, Team winningTeam);

    modifier onlyAuthorized() {
        require(authorizedProcessors[msg.sender], "Unauthorized");
        _;
    }

    function createRound(uint256 roundId, uint256 duration) external onlyAuthorized {
        rounds[roundId].id = roundId;
        rounds[roundId].status = RoundStatus.Active;
        rounds[roundId].startTime = block.timestamp;
        rounds[roundId].endTime = block.timestamp + duration;
        
        emit RoundCreated(roundId, block.timestamp);
    }

    function placeBet(uint256 roundId, Team team) external payable {
        require(rounds[roundId].status == RoundStatus.Active, "Round not active");
        require(block.timestamp < rounds[roundId].endTime, "Round ended");
        require(team != Team.None, "Invalid team");

        rounds[roundId].teamStakes[team] += msg.value;
        rounds[roundId].totalStaked += msg.value;

        emit BetPlaced(roundId, msg.sender, team, msg.value);
    }

    function completeRound(uint256 roundId, Team winningTeam) external onlyAuthorized {
        require(rounds[roundId].status == RoundStatus.Active, "Round not active");
        
        rounds[roundId].status = RoundStatus.Completed;
        rounds[roundId].winningTeam = winningTeam;

        emit RoundCompleted(roundId, winningTeam);
    }
}
