# MVC com SPA

Olá! Meu nome é Lucas, sou professor da pós-graduação da **PUC Minas**. Este é um projeto para os alunos da pós-graduação.

# Start

Crie um arquivo chamado index.html
```
<!DOCTYPE html>
<html>
<head>
  <title>Exemplo de SPA com MVC</title>
  <link rel="stylesheet" type="text/css" href="styles.css">
</head>
<body>
  <div id="app">
    <h1>Exemplo de SPA com MVC</h1>
    <form id="todo-form">
      <input type="text" id="todo-input" placeholder="Digite uma tarefa">
      <button type="submit">Adicionar</button>
    </form>
    <ul id="todo-list"></ul>
  </div>
  <script src="app.js"></script>
</body>
</html>

```
Crie o arquivo JavaScript (app.js) para implementar o padrão MVC:
```
// Modelo
const model = {
  todos: [],
  addTodo: function(todo) {
    this.todos.push(todo);
  },
};

// Visualização
const view = {
  todoList: document.getElementById('todo-list'),
  renderTodo: function(todo) {
    const todoItem = document.createElement('li');
    todoItem.textContent = todo;
    this.todoList.appendChild(todoItem);
  },
};

// Controlador
const controller = {
  init: function() {
    const todoForm = document.getElementById('todo-form');
    todoForm.addEventListener('submit', function(event) {
      event.preventDefault();
      const todoInput = document.getElementById('todo-input');
      const todo = todoInput.value;
      if (todo.trim() !== '') {
        model.addTodo(todo);
        view.renderTodo(todo);
        todoInput.value = '';
      }
    });
  },
};

// Inicialização do controlador
controller.init();
```

Neste exemplo, o modelo (model) é representado por um objeto JavaScript que contém uma lista de tarefas (todos) e uma função (addTodo) para adicionar novas tarefas à lista.

A visualização (view) é responsável por manipular o DOM e renderizar as tarefas na lista. No exemplo, cada vez que uma nova tarefa é adicionada, a função renderTodo é chamada para criar um novo elemento `li` e exibir a tarefa na lista.

O controlador (controller) é responsável por receber eventos do usuário, como o envio do formulário de adição de tarefas. Quando o formulário é enviado, o controlador obtém o valor do campo de entrada de texto, adiciona a nova tarefa ao modelo e solicita à visualização que atualize a exibição da lista.

Ao executar esse exemplo em um navegador, você terá uma aplicação básica de lista de tarefas que segue a abordagem MVC. Você pode adicionar tarefas através do formulário e vê-las sendo exibidas na lista.