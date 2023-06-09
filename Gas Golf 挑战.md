# Gas Golf

本页面是一个 Gas Golf 挑战，用于测试您在 Solidity 中编写高效合约的能力。

## 什么是 Gas？

Gas 是以太坊中的计价单位，表示执行每个操作所需的成本。在以太坊智能合约中，所有操作（存储、读取、计算等）都需要消耗一定量的 Gas。因此，编写高效的 Solidity 智能合约至关重要，可以减少成本和提高性能。

## Gas Golf 挑战

以下是一个使用 Solidity 的 `for` 循环计算数组元素总和的示例合约：

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract GasGolf {
    function calculateSum(uint[] memory numbers) public view returns (uint) {
        uint sum = 0;
        for (uint i = 0; i < numbers.length; i++) {
            sum += numbers[i];
        }
        return sum;
    }
}
```

上面的合约虽然实现了功能，但可能不够高效。您的任务是在不更改函数功能的情况下缩小该函数的 Gas 成本。以下是一个可能的解决方案：

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract GasGolf {
    function calculateSum(uint[] memory numbers) public view returns (uint) {
        uint sum = 0;
        uint length = numbers.length;
        for (uint i = 0; i < length; i++) {
            sum += numbers[i];
        }
        return sum;
    }
}
```

上面的合约将 `length` 变量用于存储数组长度，并在循环中使用变量，而不是每次都访问 `numbers.length`。由于 Solidity 编译器无法优化 `for` 循环，因此这种方法可以降低函数的 Gas 成本。

## 结论

Gas 是以太坊智能合约中的计价单位，表示执行每个操作所需的成本。编写高效的 Solidity 智能合约至关重要，可以减少成本和提高性能。通过使用变量存储数组长度并在循环中使用变量进行迭代，您可以缩小 `for` 循环的 Gas 成本。