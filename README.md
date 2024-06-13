# MyToken Smart Contract

## Overview

This Solidity smart contract implements a basic ERC-20-like token named MyToken with a token abbreviation MTK. It includes functionalities for minting and burning tokens. 

## Features

- **Token Details**: Public variables that store the token name, abbreviation, and total supply.
- **Balance Mapping**: A mapping to keep track of balances for each address.
- **Mint Function**: Allows increasing the total supply and balance of a specified address.
- **Burn Function**: Allows decreasing the total supply and balance of a specified address, with checks to prevent burning more tokens than the address holds.

## Contract Details

### Public Variables

- `tokenName`: Stores the name of the token.
- `tokenAbbrv`: Stores the abbreviation of the token.
- `totalSupply`: Stores the total supply of the token.

### Mapping

- `balances`: Maps addresses to their corresponding token balance.

### Functions

#### Mint Function

```solidity
function mint(address _to, uint256 _value) public {
    totalSupply += _value;
    balances[_to] += _value;
}
```

### Parameters
- `_to`: The address to which tokens will be minted.
- `_value`: The number of tokens to mint.

### Description
Increases the total supply by the specified _value and increases the balance of the _to address by the same amount.

#### Burn Function
```solidity
Copy code
function burn(address _from, uint256 _value) public {
    require(balances[_from] >= _value, "Insufficient balance to burn");
    totalSupply -= _value;
    balances[_from] -= _value;
}
```
### Parameters
- `_from`: The address from which tokens will be burned.
- `_value`: The number of tokens to burn.
### Description
Decreases the total supply by the specified _value and decreases the balance of the _from address by the same amount.

## Condition
The balance of the _from address must be greater than or equal to the _value to burn.

## Usage
Deploy the Contract: Deploy the contract to an Ethereum network using Remix, Truffle, Hardhat, or another development framework.
Mint Tokens: Call the mint function with the desired address and value to mint tokens.
Burn Tokens: Call the burn function with the desired address and value to burn tokens, ensuring the address has sufficient balance.

## Authors
Ayush Srivastava(ayush.blank002@gmail.com)

## License
This contract is licensed under the MIT License.
