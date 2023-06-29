# How to Simply Develop a Smart Contract

The following is an example code for a simple Solidity smart contract:

```solidity
pragma solidity ^0.8.0;

contract SimpleContract {
    uint public value;

    function setValue(uint newValue) public {
        value = newValue;
    }
}
```

This contract defines a contract called SimpleContract, which has a public variable value that can store any integer value. The contract also has a public function setValue, which can be used to set the value of value. The setValue function takes a parameter newValue, which represents the new value value. After deploying the contract, the setValue function can be used to set the value, for example:
```solidity
SimpleContract myContract = SimpleContract(0x123456...); 
myContract.setValue(100);
```

This will call the setValue function on the blockchain and set the value of value to 100.

