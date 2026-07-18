# Student-Registration-System
A responsive Student Registration System built using HTML, CSS, and JavaScript. Features include student registration, form validation, edit and delete functionality, and dynamic table updates using JavaScript.
//html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Student Registration System</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

<div class="container">
    <h2>Student Registration System</h2>

    <input type="text" id="name" placeholder="Enter Name">
    <input type="email" id="email" placeholder="Enter Email">
    <input type="text" id="course" placeholder="Enter Course">

    <button onclick="addStudent()">Register</button>

    <table id="studentTable">
        <thead>
            <tr>
                <th>Name</th>
                <th>Email</th>
                <th>Course</th>
                <th>Action</th>
            </tr>
        </thead>
        <tbody></tbody>
    </table>
</div>

<script src="script.js"></script>

</body>
</html>d



//css
body{
    font-family: Arial, sans-serif;
    background:#f2f2f2;
}

.container{
    width:600px;
    margin:40px auto;
    background:white;
    padding:20px;
    border-radius:10px;
    box-shadow:0 0 10px gray;
}

h2{
    text-align:center;
}

input{
    width:100%;
    padding:10px;
    margin:10px 0;
    box-sizing:border-box;
}

button{
    width:100%;
    padding:10px;
    background:#2196F3;
    color:white;
    border:none;
    cursor:pointer;
    font-size:16px;
}

button:hover{
    background:#0b7dda;
}

table{
    width:100%;
    margin-top:20px;
    border-collapse:collapse;
}

table,th,td{
    border:1px solid black;
}

th,td{
    padding:10px;
    text-align:center;
}

.edit{
    background:green;
    color:white;
    border:none;
    padding:5px 10px;
    margin-right:5px;
    cursor:pointer;
}

.delete{
    background:red;
    color:white;
    border:none;
    padding:5px 10px;
    cursor:pointer;
}


//javascript
function addStudent(){

    let name = document.getElementById("name").value;
    let email = document.getElementById("email").value;
    let course = document.getElementById("course").value;

    if(name=="" || email=="" || course==""){
        alert("Please fill all fields");
        return;
    }

    let table = document.getElementById("studentTable").getElementsByTagName("tbody")[0];

    let row = table.insertRow();

    row.insertCell(0).innerHTML = name;
    row.insertCell(1).innerHTML = email;
    row.insertCell(2).innerHTML = course;

    row.insertCell(3).innerHTML =
    `<button class="edit" onclick="editStudent(this)">Edit</button>
     <button class="delete" onclick="deleteStudent(this)">Delete</button>`;

    document.getElementById("name").value="";
    document.getElementById("email").value="";
    document.getElementById("course").value="";
}

function deleteStudent(btn){
    btn.parentNode.parentNode.remove();
}

function editStudent(btn){

    let row = btn.parentNode.parentNode;

    document.getElementById("name").value = row.cells[0].innerHTML;
    document.getElementById("email").value = row.cells[1].innerHTML;
    document.getElementById("course").value = row.cells[2].innerHTML;

    row.remove();
}
