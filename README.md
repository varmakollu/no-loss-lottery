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

