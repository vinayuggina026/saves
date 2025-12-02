# 📁 **Contents**

### **Module 1 – JavaScript Programs**

1. (a) Swap Case of Characters
2. (b) Most Frequent Item in Array
3. (c) Remove Duplicate Array Items
4. (d) Binary Search
5. (e) List Properties of a JS Object
6. (f) Check Object Property
7. (g) Quick Sort
8. (h) Bubble Sort
9. (i) Display JSON in HTML Table
10. (j) Student Form + GPA Table

### **Module 2 – AJAX**

11. Weather App

### **Module 3 – Node.js Programs**

12. Node Server (with user port)
13. Read File
14. Append File

### **Module 4 – MongoDB**

15. Student Database

### **Module 5 – Express + MongoDB CRUD**

16. Register / Search / Update (EJS + Express + MongoDB)

---

# 🧩 **1(a) Swap the Case of Each Character**

```js
// swapcase.js
const readline = require('readline');

var RL = readline.createInterface(process.stdin, process.stdout);

RL.question('Please Enter Text:  ', (name) => {
  let x = name;
  let y = "";

  for (let i = 0; i < x.length; i++) {
    if (x.charAt(i) >= 'A' && x.charAt(i) <= 'Z')
      y = y + x.charAt(i).toLowerCase();
    else if (x.charAt(i) >= 'a' && x.charAt(i) <= 'z')
      y = y + x.charAt(i).toUpperCase();
    else y = y + x.charAt(i);
  }

  console.log(`Output is ${y}`);
  RL.close();
});
```

---

# 🧩 **1(b) Find the Most Frequent Item in an Array**

```js
// frequent.js
var arr1 = [3, 'a', 'a', 'a', 2, 3, 'a', 3, 'a', 2, 4, 9, 3];
var mf = 1;
var m = 0;
var item;

for (var i = 0; i < arr1.length - 1; i++) {
  for (var j = i; j < arr1.length; j++) {
    if (arr1[i] == arr1[j]) m++;
    if (mf < m) {
      mf = m;
      item = arr1[i];
    }
  }
  m = 0;
}

console.log(item + " ( " + mf + " times )");
```

---

# 🧩 **1(c) Remove Duplicate Items from an Array**

```js
// removeduplicates.js
function removeDuplicates(num) {
  let unique = [];
  num.forEach((c) => {
    if (!unique.includes(c)) {
      unique.push(c);
    }
  });
  return unique;
}

let myNum = [1, 2, 2, 4, 5, 4, 7, 8, 7, 3, 6];
let result = removeDuplicates(myNum);

console.log("Original List: " + myNum);
console.log("Unique List: " + result);
```

---

# 🧩 **1(d) Perform Binary Search**

```js
// binarysearch.js
let iterativeFunction = function (arr, x) {
  let start = 0, end = arr.length - 1;

  while (start <= end) {
    let mid = Math.floor((start + end) / 2);

    if (arr[mid] === x) return true;
    else if (arr[mid] < x) start = mid + 1;
    else end = mid - 1;
  }

  return false;
};

let arr = [1, 3, 5, 7, 8, 9];
let x = 5;
console.log(iterativeFunction(arr, x));
```

---

# 🧩 **1(e) List Properties of a JavaScript Object**

```js
// objectproperties.js
let object = {
  name: 'Jack',
  age: 25,
  college: 'KMIT',
  year: 3,
  sem: 1
};

let properties = Object.keys(object);
console.log(properties);
```

---

# 🧩 **1(f) Check if an Object Contains a Given Property**

```js
// checkproperty.js
let object = { name: 'Jack', age: 25, college: 'KMIT', year: 3, sem: 1 };

console.log(object.hasOwnProperty('name'));
console.log('name' in object);
console.log(object.name);  
console.log(object.fee);
```

---

# 🧩 **1(g) Quick Sort**

```js
// quicksort.js
function quick_Sort(origArray) {
  if (origArray.length <= 1) return origArray;

  var left = [];
  var right = [];
  var pivot = origArray.pop();
  var length = origArray.length;

  for (var i = 0; i < length; i++) {
    if (origArray[i] <= pivot) left.push(origArray[i]);
    else right.push(origArray[i]);
  }

  return [].concat(quick_Sort(left), pivot, quick_Sort(right));
}

var myArray = [3, 0, 2, 5, -1, 4, 1];
console.log("Original array: " + myArray);
console.log("Sorted array: " + quick_Sort(myArray));
```

---

# 🧩 **1(h) Bubble Sort**

```js
// bubblesort.js
function swap(arr, first_Index, second_Index) {
  var temp = arr[first_Index];
  arr[first_Index] = arr[second_Index];
  arr[second_Index] = temp;
}

function bubble_Sort(arr) {
  var len = arr.length;
  for (var i = 0; i < len; i++) {
    for (var j = 0; j < len - i - 1; j++) {
      if (arr[j] > arr[j + 1]) swap(arr, j, j + 1);
    }
  }
  return arr;
}

var myArray = [3, 0, 2, 5, -1, 4, 1];
console.log("Original array: " + myArray);
console.log("Sorted array: " + bubble_Sort(myArray));
```

---

# 🧩 **1(i) Read JSON and Display Data in HTML Table**

### **s1.json**

```json
{
  "student": [
    {"name": "Bhavana", "age": 20, "college": "KMIT", "year": 3, "sem": 1},
    {"name": "Ram", "age": 21, "college": "JNTU", "year": 4, "sem": 2},
    {"name": "John", "age": 26, "college": "KMEC", "year": 1, "sem": 1},
    {"name": "Reena", "age": 19, "college": "NGIT", "year": 3, "sem": 1}
  ]
}
```

### **index.html**

```html
<!DOCTYPE html>
<html>
<head>
  <title>Convert JSON Data to HTML Table</title>
  <style>
    th, td, p, input { font:14px Verdana; }
    table, th, td { border: solid 2px #DDD; border-collapse: collapse; padding: 2px 3px; text-align: center; }
    th { font-weight:bold; }
  </style>
</head>
<body>
  <input type="button" onclick="CreateTableFromJSON()" value="Create Table From JSON" />
  <p id="showData"></p>

  <script>
    function CreateTableFromJSON() {
      fetch("s1.json")
        .then(response => response.json())
        .then(data => {
          var col = [];
          for (var i = 0; i < data.student.length; i++) {
            for (var key in data.student[i]) {
              if (col.indexOf(key) === -1) col.push(key);
            }
          }

          var table = document.createElement("table");
          var tr = table.insertRow(-1);

          col.forEach(c => {
            var th = document.createElement("th");
            th.innerHTML = c;
            tr.appendChild(th);
          });

          data.student.forEach(s => {
            tr = table.insertRow(-1);
            col.forEach(c => {
              var cell = tr.insertCell(-1);
              cell.innerHTML = s[c];
            });
          });

          document.getElementById("showData").innerHTML = "";
          document.getElementById("showData").appendChild(table);
        });
    }
  </script>
</body>
</html>
```

---

# 🧩 **1(j) Student Form (Display GPA in a Table)**

```html
<!DOCTYPE html>
<html>
<head>
  <title>Student Marks Sheet</title>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0-beta1/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>
  <div id="mydata"></div>
  <div id="myformdiv">
    <h3>Enter Student Details and Marks</h3>
    <form>
      <label>Student name:</label><input type="text" id="sname"><br><br>
      <label>Roll number:</label><input type="text" id="rollno"><br><br>
      <label>Subject 1 Marks:</label><input type="number" id="marks1"><br><br>
      <label>Subject 2 Marks:</label><input type="number" id="marks2"><br><br>
      <label>Subject 3 Marks:</label><input type="number" id="marks3"><br><br>
      <input type="button" onclick="myFunction()" value="Submit">
    </form>
  </div>

  <script>
    function myFunction() {
      document.getElementById('myformdiv').style.display = 'none';
      let avg = (parseInt(marks1.value) + parseInt(marks2.value) + parseInt(marks3.value)) / 3;
      let gpa = (avg / 10).toFixed(2);
      let info = `
        <h3>Student Details</h3>
        <table class="table table-bordered">
          <tr><td>Name</td><td>${sname.value}</td></tr>
          <tr><td>Roll No</td><td>${rollno.value}</td></tr>
          <tr><td>GPA</td><td>${gpa}</td></tr>
        </table>`;
      document.getElementById('mydata').innerHTML = info;
    }
  </script>
</body>
</html>
```

---

# 🧩 **2. Weather App (AJAX)**

```html
<!DOCTYPE html>
<html>
<head>
  <title>Weather App</title>
  <style>
    #weather { border-collapse: collapse; width: 50%; margin: 20px auto; }
    #weather th, #weather td { border: 1px solid #ddd; padding: 8px; text-align: left; }
    #weather th { background-color: #04AA6D; color: white; }
  </style>
  <script>
    function getWeather() {
      let city = document.getElementById('city').value;
      let req = new XMLHttpRequest();
      req.open('GET', 'https://api.openweathermap.org/data/2.5/weather?q=' + city + '&appid=93f26e3c57081a6210de53b8dcfdfea4', true);
      req.onload = function() {
        let data = JSON.parse(req.responseText);
        document.getElementById('country').innerHTML = data.sys.country;
        document.getElementById('temp').innerHTML = data.main.temp + ' F';
        document.getElementById('humid').innerHTML = data.main.humidity;
      };
      req.send();
    }
  </script>
</head>
<body>
  <h2 align="center">Enter City Name</h2>
  <input id="city" type="text">
  <button onclick="getWeather()">Get Weather</button>
  <table id="weather">
    <tr><th>Country</th><td id="country"></td></tr>
    <tr><th>Temperature</th><td id="temp"></td></tr>
    <tr><th>Humidity</th><td id="humid"></td></tr>
  </table>
</body>
</html>
```

---

# 🧩 **3. Node.js Server (Accept Port from User)**

```js
// server.js
var http = require('http');
var port = process.argv[2] || 8000;

var server = http.createServer(function (req, res) {
  if (req.url == '/') {
    res.writeHead(200, { 'Content-Type': 'text/html' });
    res.write('<html><body><p>This is Home Page.</p></body></html>');
    res.end();
  }
  else if (req.url == "/student") {
    res.writeHead(200, { 'Content-Type': 'text/html' });
    res.write('<html><body><p>This is Student Page.</p></body></html>');
    res.end();
  }
  else {
    res.end('Invalid Request!');
  }
});

server.listen(port);
console.log('Node.js web server at port ' + port + ' is running...');
```

---

# 🧩 **4. Read File and Display Contents**

```js
// readfile.js
var fs = require('fs');
try {
  var data = fs.readFileSync('my-file.txt', 'utf8');
  console.log(data);
} catch (e) {
  console.log('Error:', e.stack);
}
```

---

# 🧩 **5. Append or Create File**

```js
// appendfile.js
var fs = require('fs');

fs.appendFile('newfile.txt', `Learn Node FS module \r\n`, function (err) {
  if (err) throw err;
  console.log('File is Appended successfully.');
});
```

---

# 🧩 **6. MongoDB Student Database**

```bash
show dbs;
use student;
db.studentinfo.insert({name:"john",id:"20bd1a05051",course:"b.tech",branch:"cse"});
db.studentinfo.insert({name:"reena",id:"20bd1a0502",course:"M.tech",branch:"it"});
db.studentinfo.insert({name:"ram",id:"20bd1a0503",course:"b.tech",branch:"cse"});
db.studentinfo.find({});
```

Got you — you want the **actual code blocks for Sets 7, 8, and 9 included directly in the README.md**, just like your earlier sets (1–6).
Here is the **full README.md section WITH ALL CODE INCLUDED** for Sets **7, 8, and 9**.

---

# ✅ **README.md – Sets 7, 8, and 9 (Full Code Included)**

---

# 🧩 **SET 7 — Fetch Student Details (Express + MongoDB)**

## 📁 Folder Structure

```
set7/
├── app.js
├── model/
│   └── student.js
├── controller/
│   ├── searchStudent.js
│   └── searchdb.js
└── public/
    └── search.html
```

---

## ⚙️ **app.js**

```js
const express = require('express');
const mongoose = require('mongoose');
const path = require('path');
const app = express();

mongoose.connect('mongodb://localhost/student', { useNewUrlParser: true, useUnifiedTopology: true })
  .then(() => console.log('MongoDB connected'))
  .catch(err => console.log(err));

app.use(express.json());
app.use(express.urlencoded({ extended: true }));
app.use(express.static(path.join(__dirname, 'public')));

const searchStudent = require('./controller/searchStudent');
const fetchStudent = require('./controller/searchdb');

app.get('/', searchStudent);
app.post('/student/fetch', fetchStudent);

app.listen(3000, () => console.log('Server running on http://localhost:3000'));
```

---

## 🧠 **model/student.js**

```js
const mongoose = require('mongoose');

const StudentSchema = new mongoose.Schema({
  name: String,
  id: String,
  course: String,
  branch: String
});

module.exports = mongoose.model('Student', StudentSchema);
```

---

## 📜 **controller/searchStudent.js**

```js
const path = require('path');

module.exports = (req, res) => {
  res.sendFile(path.join(__dirname, '../public/search.html'));
};
```

---

## 📜 **controller/searchdb.js**

```js
const Student = require('../model/student');

module.exports = async (req, res) => {
  try {
    const rollno = req.body.rollno;
    const student = await Student.findOne({ id: rollno });

    if (!student) {
      return res.send(`<h3>No Student Found with Roll No: ${rollno}</h3>`);
    }

    res.send(`
      <h2>Student Details</h2>
      <table border="1" cellpadding="8">
        <tr><th>Name</th><th>Roll No</th><th>Course</th><th>Branch</th></tr>
        <tr>
          <td>${student.name}</td>
          <td>${student.id}</td>
          <td>${student.course}</td>
          <td>${student.branch}</td>
        </tr>
      </table>
      <br><a href="/">Search Again</a>
    `);
  } catch (error) {
    res.send('Error fetching student details.');
  }
};
```

---

## 🌐 **public/search.html**

```html
<!DOCTYPE html>
<html>
<head>
  <title>Search Student</title>
</head>
<body>
  <h2>Search Student by Roll Number</h2>
  <form action="/student/fetch" method="POST">
    <input type="text" name="rollno" placeholder="Enter Roll No" required>
    <button type="submit">Fetch Details</button>
  </form>
</body>
</html>
```

---

# 🧩 **SET 8 — CRUD Operations (Express + MongoDB)**

## 📁 Folder Structure

```
set8/
├── app.js
├── model/student.js
└── public/
    ├── index.html
    ├── add.html
    ├── search.html
    ├── update.html
    └── delete.html
```

---

## ⚙️ **app.js**

```js
const express = require('express');
const mongoose = require('mongoose');
const path = require('path');
const Student = require('./model/student');
const app = express();

mongoose.connect('mongodb://localhost/student', { useNewUrlParser: true, useUnifiedTopology: true })
  .then(() => console.log('MongoDB connected'));

app.use(express.json());
app.use(express.urlencoded({ extended: true }));
app.use(express.static(path.join(__dirname, 'public')));

app.get('/', (req, res) => res.sendFile(path.join(__dirname, 'public/index.html')));

app.post('/add', async (req, res) => {
  await Student.create(req.body);
  res.send('<h3>Student Added Successfully</h3><a href="/">Go Home</a>');
});

app.post('/search', async (req, res) => {
  const student = await Student.findOne({ id: req.body.id });
  if (student)
    res.send(`<h3>Found:</h3><p>${student.name} - ${student.course} - ${student.branch}</p>`);
  else res.send('<h3>Student Not Found</h3>');
});

app.post('/update', async (req, res) => {
  await Student.updateOne({ id: req.body.id }, { $set: req.body });
  res.send('<h3>Student Updated Successfully</h3><a href="/">Go Home</a>');
});

app.post('/delete', async (req, res) => {
  await Student.deleteOne({ id: req.body.id });
  res.send('<h3>Student Deleted Successfully</h3><a href="/">Go Home</a>');
});

app.listen(4000, () => console.log('Server running on http://localhost:4000'));
```

---

## 🧠 **model/student.js**

```js
const mongoose = require('mongoose');

const StudentSchema = new mongoose.Schema({
  name: String,
  id: String,
  course: String,
  branch: String
});

module.exports = mongoose.model('Student', StudentSchema);
```

---

## 📄 **public/index.html**

```html
<!DOCTYPE html>
<html>
<head><title>Student CRUD</title></head>
<body>
  <h2>Student CRUD Portal</h2>
  <a href="add.html">Add Student</a> |
  <a href="search.html">Search Student</a> |
  <a href="update.html">Update Student</a> |
  <a href="delete.html">Delete Student</a>
</body>
</html>
```

---

## ➕ **add.html**

```html
<h2>Add Student</h2>
<form action="/add" method="POST">
  <input name="name" placeholder="Name"><br>
  <input name="id" placeholder="Roll No"><br>
  <input name="course" placeholder="Course"><br>
  <input name="branch" placeholder="Branch"><br>
  <button type="submit">Add</button>
</form>
```

---

## 🔍 **search.html**

```html
<h2>Search Student</h2>
<form action="/search" method="POST">
  <input name="id" placeholder="Roll No" required>
  <button type="submit">Search</button>
</form>
```

---

## ✏️ **update.html**

```html
<h2>Update Student</h2>
<form action="/update" method="POST">
  <input name="id" placeholder="Roll No"><br>
  <input name="name" placeholder="New Name"><br>
  <input name="course" placeholder="New Course"><br>
  <input name="branch" placeholder="New Branch"><br>
  <button type="submit">Update</button>
</form>
```

---

## ❌ **delete.html**

```html
<h2>Delete Student</h2>
<form action="/delete" method="POST">
  <input name="id" placeholder="Roll No"><br>
  <button type="submit">Delete</button>
</form>
```

---

# 🧩 **SET 9 — CRUD Website with Routing (Express + MongoDB)**

## 📁 Folder Structure

```
set9/
├── app.js
├── routes.js
├── model/student.js
└── public/
    ├── index.html
    ├── add.html
    ├── search.html
    ├── update.html
    └── delete.html
```

---

## ⚙️ **app.js**

```js
const express = require('express');
const mongoose = require('mongoose');
const path = require('path');
const routes = require('./routes');

mongoose.connect('mongodb://localhost/student', { useNewUrlParser: true, useUnifiedTopology: true })
  .then(() => console.log('MongoDB connected'));

const app = express();
app.use(express.urlencoded({ extended: true }));
app.use(express.static(path.join(__dirname, 'public')));
app.use('/', routes);

app.listen(5000, () => console.log('Server running on http://localhost:5000'));
```

---

## 🧭 **routes.js**

```js
const express = require('express');
const router = express.Router();
const Student = require('./model/student');

router.get('/', (req, res) => res.sendFile(__dirname + '/public/index.html'));

router.post('/add', async (req, res) => {
  await Student.create(req.body);
  res.send('<h3>Student Added!</h3><a href="/">Home</a>');
});

router.post('/search', async (req, res) => {
  const student = await Student.findOne({ id: req.body.id });
  if (student)
    res.send(`<p>${student.name} - ${student.course} - ${student.branch}</p>`);
  else
    res.send('<h3>No student found!</h3>');
});

router.post('/update', async (req, res) => {
  await Student.updateOne({ id: req.body.id }, { $set: req.body });
  res.send('<h3>Student Updated!</h3><a href="/">Home</a>');
});

router.post('/delete', async (req, res) => {
  await Student.deleteOne({ id: req.body.id });
  res.send('<h3>Student Deleted!</h3><a href="/">Home</a>');
});

module.exports = router;
```

---

## 📄 **public/index.html**

```html
<h2>Student Portal</h2>
<a href="add.html">Add</a> |
<a href="search.html">Search</a> |
<a href="update.html">Update</a> |
<a href="delete.html">Delete</a>
```

---

## ➕ **add.html**

```html
<h2>Add Student</h2>
<form action="/add" method="POST">
  <input name="name" placeholder="Name"><br>
  <input name="id" placeholder="Roll No"><br>
  <input name="course" placeholder="Course"><br>
  <input name="branch" placeholder="Branch"><br>
  <button type="submit">Add</button>
</form>
```

---

## 🔍 **search.html**

```html
<h2>Search Student</h2>
<form action="/search" method="POST">
  <input name="id" placeholder="Roll No">
  <button type="submit">Search</button>
</form>
```

---

## ✏️ **update.html**

```html
<h2>Update Student</h2>
<form action="/update" method="POST">
  <input name="id" placeholder="Roll No"><br>
  <input name="name" placeholder="Name"><br>
  <input name="course" placeholder="Course"><br>
  <input name="branch" placeholder="Branch"><br>
  <button type="submit">Update</button>
</form>
```

---

## ❌ **delete.html**

```html
<h2>Delete Student</h2>
<form action="/delete" method="POST">
  <input name="id" placeholder="Roll No">
  <button type="submit">Delete</button>
</form>
```
