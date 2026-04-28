# Automated-Market-Maker-with-Liquidity-Provider-Tokens
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.26;

contract BasicAMMWithLP {
    uint256 public reserveA;
    uint256 public reserveB;
    uint256 public totalLiquidity;

    mapping(address => uint256) public liquidityProvided;

    event LiquidityAdded(address provider, uint256 amountA, uint256 amountB);
    event Swapped(address user, uint256 amountIn, uint256 amountOut);

    function addLiquidity(uint256 amountA, uint256 amountB) public payable {
        reserveA += amountA;
        reserveB += amountB;
        uint256 liquidityMinted = amountA; // simplified
        liquidityProvided[msg.sender] += liquidityMinted;
        totalLiquidity += liquidityMinted;
        emit LiquidityAdded(msg.sender, amountA, amountB);
    }
}
