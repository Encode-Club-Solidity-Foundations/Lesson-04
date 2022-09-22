# Lesson 4 - Interfaces and external calls
## External calls
* What is a “MethodID”
* Fallback and receive functions
* External calls
### References
https://docs.soliditylang.org/en/latest/control-structures.html#external-function-calls

https://solidity-by-example.org/function-selector/

## Using interfaces
* Fallback and receive functions
* External calls
* Attaching “mismatched” contracts
* Why some functions work and others don’t because of the “MethodID”

### Restricting access to functions
* Wrapping up contents
  * Modifier
  * Assertion inside modifiers
  * Message Sender
  * Visibility
  * Mutability
* Implementing basic access control on _setText_
### References
https://docs.soliditylang.org/en/latest/common-patterns.html#restricting-access

<pre><code>// SPDX-License-Identifier: GPL-3.0
pragma solidity >=0.7.0 <0.9.0;

contract HelloWorld {
    string private text;
    address public owner;

    constructor() {
        text = "Hello World";
        owner = msg.sender;
    }

    function helloWorld() public view returns (string memory) {
        return text;
    }

    function setText(string calldata newText) public onlyOwner {
        text = newText;
    }

    function transferOwnership(address newOwner) public onlyOwner {
        owner = newOwner;
    }

    modifier onlyOwner()
    {
        require (msg.sender == owner, "Caller is not the owner");
        _;
    }
}
</code></pre>

## Contract interaction
* Interacting with previously deployed contracts using interfaces
* Inspecting “MethodId” mismatch and fallback functions
* Inspecting execution errors based on assertions
* Fixing the interfaces
* Interacting with other peoples contract

## Extra reference material
* Handy reference sheet: [Solidity Cheatsheet](https://docs.soliditylang.org/en/latest/cheatsheet.html) 
* Overall style guide: [Solidity Style Guide](https://docs.soliditylang.org/en/latest/style-guide.html)
* Solidity quick guide: [Learn Solidity in Y minutes](https://learnxinyminutes.com/docs/solidity/)
* Typescript quick guide: [Learn Typescript in Y minutes](https://learnxinyminutes.com/docs/typescript/)

# Homework
* Create Github Issues with your questions about this lesson
* Read the references

# Weekend Project
* Form groups of 3 to 5 students
* Interact with “HelloWorld.sol” within your group to change message strings and change owners
* Write a report with each function execution and the transaction hash, if successful, or the revert reason, if failed