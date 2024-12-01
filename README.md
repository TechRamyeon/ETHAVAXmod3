# EmiruToken Smart Contract

## Overview
EmiruToken is a customizable ERC20 token built using OpenZeppelin libraries. It allows for token minting by the owner, controlled burning by users, and standard token transfer functionality. This README provides an overview of the contract's features and instructions for deployment and usage.

## Features
1. **ERC20 Token Standard**: Implements the standard ERC20 token interface for fungible tokens.
2. **Customizable Name and Symbol**: The token name and symbol are set during deployment.
3. **Minting**: The contract owner can mint new tokens to specified addresses.
4. **Burning**: Users can burn up to 10 tokens per transaction.
5. **Custom Transfer Logic**: Overrides the `transfer` function for standard token transfers.

## Contract Details

- **Token Name**: Set during deployment.
- **Token Symbol**: Set during deployment.
- **Token Decimals**: 18 (default for ERC20 tokens).

## Deployment

### Prerequisites
1. **Node.js**: Install [Node.js](https://nodejs.org/) and [npm](https://www.npmjs.com/).
2. **Hardhat**: Install Hardhat for compiling and deploying the contract.
3. **Solidity Compiler**: Ensure Solidity version `^0.8.18` is compatible.

### Steps
1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Compile the contract:
   ```bash
   npx hardhat compile
   ```
4. Deploy the contract:
   ```bash
   npx hardhat run scripts/deploy.js --network <network-name>
   ```

## Functions

### Token Operations
- **`mint(address to, uint256 amount)`**
  - Mints new tokens to the specified address.
  - Only callable by the contract owner.
- **`burn(uint256 amount)`**
  - Allows users to burn tokens from their balance.
  - A maximum of 10 tokens can be burned per transaction. Transactions attempting to burn more will be rejected.
- **`transfer(address to, uint256 amount)`**
  - Transfers tokens from the sender to the specified address.

## Usage Example

### Minting Tokens
The contract owner can mint tokens:
```solidity
mint(address recipient, uint256 amount);
```

### Burning Tokens
Users can burn up to 10 tokens per transaction:
```solidity
burn(uint256 amount);
```

### Transferring Tokens
Users can transfer tokens to another address:
```solidity
transfer(address to, uint256 amount);
```

## Security Notes
1. The contract uses OpenZeppelin's `Ownable` for ownership management.
2. Ensure proper access control to the `mint` function to avoid unauthorized token creation.
3. The `burn` function includes a safeguard limiting the burn amount to 10 tokens per transaction.

## License
This project is licensed under the [MIT License](https://opensource.org/licenses/MIT). 
