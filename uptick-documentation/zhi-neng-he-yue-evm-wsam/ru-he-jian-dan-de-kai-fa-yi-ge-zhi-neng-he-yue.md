# 如何简单的开发一个智能合约

&#x20; 以下是一个简单的Solidity智能合约的示例代码：

```solidity
pragma solidity ^0.8.0;

contract SimpleContract {
    uint public value;

    function setValue(uint newValue) public {
        value = newValue;
    }
}
```

这个合约定义了一个名为SimpleContract的合约，它有一个公共变量value，可以存储任意整数值。合约还有一个公共函数setValue，可以用于设置value的值。setValue函数接受一个参数newValue，表示新的value值。  在部署合约后，可以使用setValue函数来设置value的值，例如：

```solidity
SimpleContract myContract = SimpleContract(0x123456...); // 合约地址
myContract.setValue(100);
```

&#x20;这将在区块链上调用setValue函数，并将value的值设置为100。

