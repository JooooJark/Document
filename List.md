<!DOCTYPE html>
<html>
<head>
    <title>To-Do List</title>
</head>
<body>
    <h1>To-Do List</h1>
    <input type="text" id="taskInput" placeholder="Enter task">
    <button onclick="addTask()">Add Task</button>
    <ul id="taskList"></ul>

    <script>
        function addTask() {
            let input = document.getElementById("taskInput");
            let task = input.value;
            if (!task) return;

            let tasks = JSON.parse(localStorage.getItem("tasks")) || [];
            tasks.push(task);
            localStorage.setItem("tasks", JSON.stringify(tasks));

            displayTasks();
            input.value = "";
        }

        function displayTasks() {
            let tasks = JSON.parse(localStorage.getItem("tasks")) || [];
            let list = document.getElementById("taskList");
            list.innerHTML = "";
            tasks.forEach((task, index) => {
                list.innerHTML += `<li>${task} <button onclick="deleteTask(${index})">Delete</button></li>`;
            });
        }

        function deleteTask(index) {
            let tasks = JSON.parse(localStorage.getItem("tasks")) || [];
            tasks.splice(index, 1);
            localStorage.setItem("tasks", JSON.stringify(tasks));
            displayTasks();
        }

        displayTasks();
    </script>
</body>
</html>
