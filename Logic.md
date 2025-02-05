const todos = [];

function addTodo(task) {
    todos.push({ task, done: false });
}

function markDone(index) {
    if (todos[index]) {
        todos[index].done = true;
    }
}

function listTodos() {
    console.log("Your To-Do List:");
    todos.forEach((todo, i) => {
        console.log(`${i + 1}. [${todo.done ? 'x' : ' '}] ${todo.task}`);
    });
}

addTodo("Learn JavaScript");
addTodo("Build a project");
markDone(0);
listTodos();
