# JointSavings Smart Contract

To automate the creation of joint savings accounts, this solidity smart contract accepts two user addresses. These addresses will be able to control a joint savings account. The smart contract uses ether management functions to implement a financial institution’s requirements for providing the features of the joint savings account. These features consist of the ability to deposit and withdraw funds from the account.

---

## Code
```
pragma solidity ^0.5.0;
contract JointSavings {
    address payable accountOne;
    address payable accountTwo;
    address public lastToWithdraw;
    uint public lastWithdrawAmount;
    uint public contractBalance;

    function withdraw(uint amount, address payable recipient) public {
        require(recipient == accountOne || recipient == accountTwo, "You don't own this account!");
        require(contractBalance > amount, "Insufficient funds!");

        if (lastToWithdraw != recipient) {
            lastToWithdraw = recipient;
        }

        recipient.transfer(amount);
        lastWithdrawAmount = amount;
        contractBalance  = address(this).balance;
    }

    function deposit() public payable {
        contractBalance = address(this).balance;
    }

    function setAccounts(address payable account1, address payable account2) public{
        accountOne = account1;
        accountTwo = account2;
    }

    function() external payable {}
}
```
---

## Compile and Deploy

![Compile](https://github.com/stipptracie/JointSavings/blob/main/ExecutionResults/compiledJointSavings.png)

![Deploy](https://github.com/stipptracie/JointSavings/blob/main/ExecutionResults/DeployedContract.png)


---

## Execution Results

### Set Account Addresses:
![SetAccounts](https://github.com/stipptracie/JointSavings/blob/main/ExecutionResults/setAccounts.png)

### Deposits:
![Deposit1](https://github.com/stipptracie/JointSavings/blob/main/ExecutionResults/1ethinweideposit.png)

![Deposit2](https://github.com/stipptracie/JointSavings/blob/main/ExecutionResults/5ethdeposit.png)

![Deposit3](https://github.com/stipptracie/JointSavings/blob/main/ExecutionResults/10ethinweideposit.png)

![BalanceAfterDeposits](https://github.com/stipptracie/JointSavings/blob/main/ExecutionResults/balanceAfterDeposits.png)

### Withdrawls:
![Withdrawl1](https://github.com/stipptracie/JointSavings/blob/main/ExecutionResults/firstWithdrawl.png)

![Withdrawl2](https://github.com/stipptracie/JointSavings/blob/main/ExecutionResults/secondWithdrawl.png)

---

## Project by:
> email: stipptracie@gmail.com |
> [GitHub](https://github.com/stipptracie) |
> [LinkedIn](https://www.linkedin.com/in/tracie-stipp-0719691b/)

---
