// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract MyZKEVMToken is ERC20, Ownable {
    // Конструктор токена за потреби можна змінити
    constructor() ERC20("Cryptojeka", "CRYPJ") Ownable(msg.sender) {
        // Початкова емісія токенів відправляється власнику контракту
        _mint(msg.sender, 1000000 * 10 ** decimals());
    }

    // Функція для створення додаткових токенів (може викликати тільки власник)
    function mint(address to, uint256 amount) public onlyOwner {
        _mint(to, amount);
    }

    // Функція для спалювання токенів
    function burn(uint256 amount) public {
        _burn(msg.sender, amount);
    }
}
