# Types of Function

This Solidity program is a token contract that implements the ERC20 standard. It allows the creation, transfer, and burning of tokens. The purpose of this contract is to serve as a template for creating custom tokens on the Ethereum blockchain.

## Description

This contract is implemented in Solidity, a programming language used for developing smart contracts on the Ethereum blockchain. The contract extends the ERC20 contract from the OpenZeppelin library, which provides a standardized interface for tokens on the Ethereum network. The contract also includes an additional modifier, `onlyOwner`, to restrict certain functions to be called only by the contract owner.

## Getting Started

### Prerequisites

To deploy and interact with this contract, you will need:

- A development environment such as Remix or Truffle.
- Access to an Ethereum network (local or testnet) to deploy the contract.
- The OpenZeppelin library installed.

### Deployment

1. Open your preferred Solidity development environment (e.g., Remix).
2. Create a new Solidity file and save it with a .sol extension (e.g., MyToken.sol).

   // SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract MyToken is ERC20 {
    address private _owner; // Private variable to store the contract owner's address

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract MyToken is ERC20 {
    address private _owner;

    constructor() ERC20("BigCoin", "BGC") {
        _owner = msg.sender;
    }

    modifier onlyOwner() {
        require(msg.sender == _owner, "Only the contract owner can call this function");
        _;
    }

    function mint(address account, uint256 amount) external onlyOwner {
        _mint(account, amount);
    }

    function burn(uint256 amount) external {
        _burn(msg.sender, amount);
    }

    function transfer(address reciever, uint256 amount) public override returns (bool) {
        _transfer(msg.sender, reciever, amount);
        require(balanceOf(msg.sender) >= amount, "Insufficient balance");
        return true;
    }
}
```
3. Copy and paste the code from the provided code snippet into the file.
4. Make sure you have the OpenZeppelin library imported correctly.
5. Compile the contract using the appropriate Solidity compiler version (e.g., 0.8.0).
6. Deploy the contract to your desired Ethereum network, ensuring that you have sufficient funds to cover deployment costs.
7. Take note of the deployed contract's address for future interactions.

### Interacting with the Contract

Once the contract is deployed, you can interact with it using various methods. Here are a few examples:

- *Minting Tokens*: Only the contract owner can mint new tokens. Use the `mint` function, providing the recipient's address and the amount of tokens to be minted.

- *Transferring Tokens*: Use the `transfer` function to transfer tokens from your address to another address. Provide the recipient's address and the amount of tokens to transfer.

- *Burning Tokens*: To destroy tokens from your address, use the `burn` function and specify the amount of tokens to burn.

Please refer to the Solidity documentation for more information on interacting with ERC20 contracts.

## Authors

Sutirtho Chakravorty

[Email ID](mailto:sutirthochakravorty@gmail.com)

## License

This project is licensed under the MIT License.
