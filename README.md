MyToken Solidity Smart Contract
Overview
The MyToken contract is a basic implementation of an Ethereum token. This contract includes functions for minting and burning tokens, maintaining balances for different addresses, and keeping track of the total supply of tokens. The token details (name and abbreviation) are hardcoded for simplicity.

Requirements
Public Variables:

Store the details about the token (Token Name, Token Abbrv., Total Supply).
Mapping:

Maintain a mapping of addresses to balances (address => uint).
Mint Function:

Increase the total supply by a specified number and increase the balance of a specified address by the same amount.
Burn Function:

Decrease the total supply by a specified number and decrease the balance of a specified address by the same amount.
Ensure the balance of the specified address is greater than or equal to the amount to be burned.
Contract Code
solidity
Copy code
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

/*
       REQUIREMENTS
    1. Your contract will have public variables that store the details about your coin (Token Name, Token Abbrv., Total Supply)
    2. Your contract will have a mapping of addresses to balances (address => uint)
    3. You will have a mint function that takes two parameters: an address and a value. 
       The function then increases the total supply by that number and increases the balance 
       of the “sender” address by that amount
    4. Your contract will have a burn function, which works the opposite of the mint function, as it will destroy tokens. 
       It will take an address and value just like the mint functions. It will then deduct the value from the total supply 
       and from the balance of the “sender”.
    5. Lastly, your burn function should have conditionals to make sure the balance of "sender" is greater than or equal 
       to the amount that is supposed to be burned.
*/

contract MyToken {
    // Public variables to store token details
    string public tokenName = "MyToken";
    string public tokenAbbrv = "MTK";
    uint256 public totalSupply;

    // Mapping to store balances
    mapping(address => uint256) public balances;

    // Mint function to increase total supply and balance of the sender address
    function mint(address _to, uint256 _value) public {
        totalSupply += _value;
        balances[_to] += _value;
    }

    // Burn function to decrease total supply and balance of the sender address
    function burn(address _from, uint256 _value) public {
        require(balances[_from] >= _value, "Insufficient balance to burn");
        totalSupply -= _value;
        balances[_from] -= _value;
    }
}
Detailed Explanation
License Declaration:

// SPDX-License-Identifier: MIT: Specifies the contract's license type as MIT.
Pragma Directive:

pragma solidity 0.8.18;: Specifies the Solidity compiler version used to compile the contract.
Contract Declaration:

contract MyToken: Defines the smart contract named MyToken.
Public Variables:

string public tokenName = "MyToken";: A public variable that stores the name of the token.
string public tokenAbbrv = "MTK";: A public variable that stores the abbreviation of the token.
uint256 public totalSupply;: A public variable that stores the total supply of the token. Initialized to 0.
Mapping for Balances:

mapping(address => uint256) public balances;: A public mapping that maps addresses to their respective token balances.
Mint Function:

function mint(address _to, uint256 _value) public: A public function that mints new tokens.
Increases the totalSupply by _value.
Increases the balance of the _to address by _value.
Burn Function:

function burn(address _from, uint256 _value) public: A public function that burns tokens.
require(balances[_from] >= _value, "Insufficient balance to burn");: Ensures the _from address has enough tokens to burn.
Decreases the totalSupply by _value.
Decreases the balance of the _from address by _value.
Usage
Minting Tokens:

Call the mint function with the recipient's address and the amount of tokens to mint.
solidity
Copy code
mint(address _to, uint256 _value)
Burning Tokens:

Call the burn function with the sender's address and the amount of tokens to burn.
solidity
Copy code
burn(address _from, uint256 _value)
License
This project is licensed under the MIT License.
