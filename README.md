# week-05 : To-do-list 
## author
-**benard mwangi wambui**
-**GitHub**b4130478-web
-**2 may 2026
## project description 
a to-do-list
## technologies used
-html5
-Dom
-css
## how to run
- clone these repository
- run index.html
- <!DOCTYPE html>
<html>
<body>
<h2>To-Do List</h2>

<input id="task" placeholder="New task">
<button onclick="addTask()">Add</button>
<ul id="list"></ul>
<button onclick="clearAll()">Clear All</button>

<script>
// JavaScript goes here
  
// Create a task Array
let tasks = [];

// Function to Display tasks
function displayTasks() {
  let html = "";
  for (let i = 0; i < tasks.length; i++) {
    html += "<li>" + tasks[i] +
    " <button onclick='removeTask(" + i + ")'>x</button></li>";
  }
  document.getElementById("list").innerHTML = html;
}

// Function to Add a task
function addTask() {
  let taskInput = document.getElementById("task");
  let text = taskInput.value;
  if (text === "") {
    return;
  }
  tasks.push(text);
  taskInput.value = "";
  saveTasks();
  displayTasks();
}

// Function to Remove a task
function removeTask(i) {
  tasks.splice(i, 1);
  saveTasks();
  displayTasks();
}

// Function to Clear all tasks
function clearAll() {
  tasks = [];
  saveTasks();
  displayTasks();
}

// Function to Save tasks
function saveTasks() {
  localStorage.setItem("tasks", JSON.stringify(tasks));
}

// Function to Load tasks
function loadTasks() {
  let saved = localStorage.getItem("tasks");
  if (saved !== null) {
    tasks = JSON.parse(saved);
  }
}

// Load and display tasks when page loads
loadTasks();
displayTasks()

</script>
  <style>
  h2{
    color :purple;
  }
  button{
    color:blue;
  }
  input{
    color:green
  }
  </style>

</body>
</html>

