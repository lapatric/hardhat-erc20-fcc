## Building ERC20 Tokens

An ERC20 token contract keeps track of [fungible tokens](https://docs.openzeppelin.com/contracts/4.x/tokens#different-kinds-of-tokens): any one token is exactly equal to any other token; no tokens have special rights or behavior associated with them. This makes ERC20 tokens useful for things like a *medium of exchange currency, voting rights, staking*, and more.

## OpenZeppelin

[OpenZeppelin Contracts](https://docs.openzeppelin.com/contracts) provides many ERC20-related contracts. On the [API reference](https://docs.openzeppelin.com/contracts/4.x/api/token/erc20) you’ll find detailed information on their properties and usage. Using the OpenZeppelin package we can easily implement our own ERC20 token.

```bash
# install openzeppelin/contracts package
yarn add --dev @openzeppelin/contracts
```

OpenZeppelin's conctracts are often used via inheritance, and here we’re reusing [`ERC20`](https://docs.openzeppelin.com/contracts/4.x/api/token/erc20#erc20) for both the basic standard implementation and the [`name`](https://docs.openzeppelin.com/contracts/4.x/api/token/erc20#ERC20-name--), [`symbol`](https://docs.openzeppelin.com/contracts/4.x/api/token/erc20#ERC20-symbol--), and [`decimals`](https://docs.openzeppelin.com/contracts/4.x/api/token/erc20#ERC20-decimals--) optional extensions. Additionally, we’re creating an `initialSupply` of tokens, which will be assigned to the address that deploys the contract.

```solidity
// contracts/GLDToken.sol
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract GLDToken is ERC20 {
    constructor(uint256 initialSupply) ERC20("Gold", "GLD") {
        _mint(msg.sender, initialSupply);
    }
}
```