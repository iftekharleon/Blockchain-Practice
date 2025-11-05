// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract StudentManager{
  struct Student{
    string name;
    uint score;
    address wallet;
  }

  Student[] public students;
  address public owner;
  mapping(address => uint) public studentIndex;

  constructor(){
    owner = msg.sender;
  }

  modifier onlyOwner(){
    require(msg.sender == owner);
    _;
  }
  event StudentAdded(string name, uint score, address wallet);
  event ScoreUpdated(address wallet, uint newScore);

  function addStudent(string memory _name, uint _score, address wallet) public {
    Student memory newStudent = Student(_name, _score, wallet);
    students.push(newStudent);
    studentIndex[wallet] = students.length - 1;
    emit StudentAdded(_name, _score, wallet);
  }
  function getStudent(uint _index) public view returns(Student memory){
    return students[_index];
  }
  function updateScore(uint _index, uint _score) public onlyOwner{
    students[_index].score = _score;

    emit ScoreUpdated(students[_index].wallet, _score);
  }
  function removeStudent(uint _index) public onlyOwner {
    delete students[_index];
  }

  function getStudentByAddress (address wallet) public view returns(Student memory){
    uint index = studentIndex[wallet];
    return students[index];
  }

}
