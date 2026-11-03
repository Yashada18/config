# Bank Smart Contract

## Solidity Code

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract Bank {
    uint public balance;

    // Deposit Ether
    function deposit() public payable {
        balance += msg.value;
    }

    // Withdraw Ether
    function withdraw(uint amount) public {
        require(balance >= amount, "Insufficient balance");

        balance -= amount;

        (bool success, ) = payable(msg.sender).call{value: amount}("");
        require(success, "Transfer failed");
    }

    // Check balance
    function showBalance() public view returns (uint) {
        return balance;
    }
}


## 2. Bank Smart Contract — Simple Withdrawal Version

```markdown
# Bank Smart Contract

## Solidity Code

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract Bank {
    uint public balance;

    // Deposit Ether
    function deposit() public payable {
        balance += msg.value;
    }

    // Withdraw Ether in Ether units
    function withdraw(uint amount) public {
        uint amountWei = amount * 1 ether;

        require(balance >= amountWei, "Insufficient balance");

        balance -= amountWei;

        (bool success, ) = payable(msg.sender).call{value: amountWei}("");
        require(success, "Transfer failed");
    }

    // Check balance
    function showBalance() public view returns (uint) {
        return balance;
    }
}
