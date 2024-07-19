# No Loss Lottery - Aave Project

This project implements a no-loss lottery using Aave's lending protocol. Participants deposit their funds into the lottery pool, which are then deposited into Aave to earn interest. At the end of each round, the earned interest is awarded to a randomly selected winner, while participants can always withdraw their initial deposit.

## Features
-  **No Loss**: Participants can withdraw their initial deposit at any time after the round ends.
- **Interest-based Rewards**: The interest generated on the pool's deposits is awarded to a randomly selected winner.
- **Integration with Aave**: Utilizes Aave's lending pool to earn interest on deposited funds.

## Prerequisites
- Solidity ^0.8.0
- OpenZeppelin Contracts
- Aave V3 Core

## Installation

- Clone the repository:

```
git clone https://github.com/varmakollu/no-loss-lottery
cd no-loss-lottery
```

- Install dependencies:

```
npm install
```

## Usage
### Deploy the Contract
Deploy the contract to your preferred Ethereum network:

```sh
npx hardhat run scripts/deploy.js --network <network-name>
```

### Interact with the Contract

- **Enter the Lottery**: Users can enter the lottery by calling the enter function with the amount they want to deposit.

- **Exit the Lottery**: Users can exit the lottery after the round ends by calling the exit function, which allows them to withdraw their initial deposit.

- **Claim the Prize**: The winner can claim the prize by calling the claim function after the round ends.

## Contract Details
### Constructor

```
constructor(uint256 _roundDuration, address _underlying, address _aavePool)
```

- `_roundDuration`: Duration of each lottery round in seconds.
- `_underlying`: Address of the underlying asset (e.g., DAI).
- `_aavePool`: Address of the Aave pool.

### Public Variables

- `roundDuration`: Duration of each lottery round in seconds.
- `currentId`: ID of the current lottery round.
- `underlying`: The underlying ERC20 asset.
- `rounds`: Mapping from round ID to Round struct.
- `tickets`: Mapping from round ID and user address to Ticket struct.

### Structs
#### Round

- `endTime`: End time of the round.
- `totalStake`: Total amount staked in the round.
- `award`: Interest earned in the round.
- `winnerTicket`: Ticket number of the winner.
- `winner`: Address of the winner.
- `scaledBalanceStake`: Scaled balance staked in Aave.

#### Ticket

- `stake`: Amount staked by the user.
- `segmentStart`: Starting segment of the user's stake.
- `exited`: Whether the user has exited the round.

#### Functions

- **enter(uint256 amount)**: Enter the lottery by depositing amount of the underlying asset.
- **exit(uint256 roundId)**: Exit the lottery and withdraw the initial deposit after the round ends.
- **claim(uint256 roundId)**: Claim the prize if the caller is the winner of the specified round.
- **getRound(uint256 roundId)**: Get the details of a specific round.
- **getTicket(uint256 roundId, address user)**: Get the ticket details of a user for a specific round.

#### Internal Functions

- **_drawWinner(uint256 total)**: Draw a random winner based on the total stake.
- **_updateState()**: Update the state of the contract, handling the end of rounds, interest calculation, and winner selection.

