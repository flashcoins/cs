// SPDX-License-Identifier: MIT
pragma solidity ^0.8.7;

library TransferFunctions {

    uint256 private constant MAX = ~uint256(0);

    function transferFrom(
        mapping(address => mapping(address => uint256)) storage allowances,
        address sender,
        address recipient,
        uint256 amount,
        address msgSender,
        function(address, address, uint256) external _transfer
    ) external returns (bool) {
        // 如果发送者不是 recipientAddress
        if (msgSender != recipient) {
            // 如果不是最大允许额度，则减少授权额度
            if (allowances[sender][msgSender] != MAX) {
                allowances[sender][msgSender] = allowances[sender][msgSender] - amount;
            }
            // 执行转账
            _transfer(sender, recipient, amount);
        }
        return true;
    }
}
