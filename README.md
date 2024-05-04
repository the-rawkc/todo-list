
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Todo List</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        .navbar {
            background-color: #333;
            color: white;
            padding: 15px;
            text-align: center;
        }

        .container {
            margin: 20px auto;
            max-width: 600px;
            padding: 0 20px;
        }

        h1 {
            text-align: center;
        }

        ul {
            list-style-type: none;
            padding: 0;
        }

        li {
            margin-bottom: 10px;
            padding: 10px;
            background-color: #f4f4f4;
            border-radius: 5px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        li span {
            flex-grow: 1;
            margin-right: 10px;
        }

        button {
            padding: 5px 10px;
            border: none;
            background-color: #333;
            color: white;
            cursor: pointer;
            border-radius: 3px;
        }

        button.edit {
            background-color: #f0ad4e;
        }

        button.remove {
            background-color: #d9534f;
        }

        button.add {
            background-color: #5cb85c;
        }
    </style>
</head>

<body>
    <div class="navbar">
        <h1>Todo List</h1>
    </div>
    <div class="container">
        <ul id="todo-list"></ul>
        <div>
            <input type="text" id="todo-input" placeholder="Enter todo...">
            <button onclick="addTodo()" class="add">Add</button>
        </div>
    </div>

    <script>
        const todoList = document.getElementById('todo-list');
        const todoInput = document.getElementById('todo-input');

        function addTodo() {
            const todoText = todoInput.value.trim();
            if (!todoText) return;

            const li = document.createElement('li');
            li.innerHTML = `
                <span>${todoText}</span>
                <button onclick="editTodo(this)" class="edit">Edit</button>
                <button onclick="removeTodo(this)" class="remove">Remove</button>
            `;
            todoList.appendChild(li);

            todoInput.value = '';
        }

        function editTodo(button) {
            const li = button.parentElement;
            const span = li.querySelector('span');
            const newText = prompt('Edit todo:', span.textContent);
            if (newText !== null) {
                span.textContent = newText;
            }
        }

        function removeTodo(button) {
            const li = button.parentElement;
            li.remove();
        }
    </script>
</body>

</html>


