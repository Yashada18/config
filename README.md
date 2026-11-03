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


# Students Smart Contract

## Solidity Code

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract Students {
    struct Student {
        uint id;
        string name;
        uint age;
        string course;
    }

    Student[] public students;

    // Add a student
    function addStudent(
        uint _id,
        string memory _name,
        uint _age,
        string memory _course
    ) public {
        students.push(Student(_id, _name, _age, _course));
    }

    // Get student details
    function getStudent(uint index)
        public
        view
        returns (uint, string memory, uint, string memory)
    {
        Student memory s = students[index];
        return (s.id, s.name, s.age, s.course);
    }

    // Get total number of students
    function getStudentCount() public view returns (uint) {
        return students.length;
    }
}
