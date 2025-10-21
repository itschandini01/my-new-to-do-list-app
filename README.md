# my-new-to-do-list-app
This is my new to do list app for learning new things
todo--app
todo-app/
├── index.html
├── style.css
└── script.js

Index.html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>To-Do List App</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>

  <div class="app-container">
    <h1>📝 To-Do List</h1>
    <div class="input-container">
      <input type="text" id="taskInput" placeholder="Enter your task..." />
      <button id="addBtn">Add</button>
    </div>

    <ul id="taskList"></ul>
  </div>

  <script src="script.js"></script>
</body>
</html>



style.css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background-color: #f3f3f3;
  display: flex;
  justify-content: center;
  align-items: flex-start;
  padding-top: 60px;
  min-height: 100vh;
}

.app-container {
  background-color: white;
  padding: 30px 40px;
  border-radius: 10px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
  width: 100%;
  max-width: 500px;
}

h1 {
  text-align: center;
  margin-bottom: 20px;
  color: #333;
}

.input-container {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}

#taskInput {
  flex-grow: 1;
  padding: 10px;
  font-size: 16px;
  border: 2px solid #ccc;
  border-radius: 5px;
}

#addBtn {
  padding: 10px 20px;
  background-color: #28a745;
  color: white;
  border: none;
  font-size: 16px;
  border-radius: 5px;
  cursor: pointer;
}

#addBtn:hover {
  background-color: #218838;
}

ul {
  list-style: none;
}

li {
  background-color: #f9f9f9;
  padding: 12px 15px;
  margin-bottom: 10px;
  border-radius: 5px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  transition: 0.2s;
}

li.completed span {
  text-decoration: line-through;
  color: #888;
}

.task-buttons button {
  background-color: transparent;
  border: none;
  cursor: pointer;
  font-size: 14px;
  margin-left: 10px;
}

.task-buttons .complete {
  color: #28a745;
}

.task-buttons .delete {
  color: #dc3545;
}



scipt.js

const taskInput = document.getElementById("taskInput");
const addBtn = document.getElementById("addBtn");
const taskList = document.getElementById("taskList");

addBtn.addEventListener("click", addTask);
taskInput.addEventListener("keydown", function(e) {
  if (e.key === "Enter") addTask();
});

function addTask() {
  const taskText = taskInput.value.trim();
  if (taskText === "") {
    alert("Please enter a task.");
    return;
  }

  const li = document.createElement("li");

  const span = document.createElement("span");
  span.textContent = taskText;

  const btnContainer = document.createElement("div");
  btnContainer.className = "task-buttons";

  const completeBtn = document.createElement("button");
  completeBtn.textContent = "✔️";
  completeBtn.className = "complete";
  completeBtn.onclick = () => {
    li.classList.toggle("completed");
  };

  const deleteBtn = document.createElement("button");
  deleteBtn.textContent = "❌";
  deleteBtn.className = "delete";
  deleteBtn.onclick = () => {
    taskList.removeChild(li);
  };

  btnContainer.appendChild(completeBtn);
  btnContainer.appendChild(deleteBtn);

  li.appendChild(span);
  li.appendChild(btnContainer);

  taskList.appendChild(li);
  taskInput.value = "";
}


