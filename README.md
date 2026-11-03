/*
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

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;
contract StudentData {
// Structure
struct Student {
uint rollNo;
string name;
uint age;
string course;
}
// Array
Student[] public students;
// Add student
function addStudent(
uint _rollNo,
string memory _name,
uint _age,
string memory _course
) public {
students.push(Student(_rollNo, _name, _age, _course));
}
// Get student
function getStudent(uint _index)
public
view
returns (uint, string memory, uint, string memory)
{
Student memory s = students[_index];
return (s.rollNo, s.name, s.age, s.course);
}
// Fallback
fallback() external {}
}
*/
