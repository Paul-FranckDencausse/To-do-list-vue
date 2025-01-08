<template>
    <div id="app">
      <h1>Liste de tâches</h1>
      <div class="input-container">
        <input v-model="newTodo" @keyup.enter="addTodo" placeholder="Ajouter une nouvelle tâche" />
        <button @click="addTodo">Ajouter</button>
      </div>
      <ul>
        <li v-for="(todo, index) in todos" :key="index" class="todo-item">
          {{ todo }}
          <button @click="removeTodo(index)" class="remove-button">Supprimer</button>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        newTodo: '',
        todos: []
      };
    },
    methods: {
      addTodo() {
        if (this.newTodo.trim() !== '') {
          this.todos.push(this.newTodo);
          this.newTodo = '';
        }
      },
      removeTodo(index) {
        this.todos.splice(index, 1);
      }
    }
  };
  </script>
  
  <style scoped>
  #app {
    font-family: Arial, sans-serif;
    max-width: 600px;
    margin: 0 auto;
    padding: 20px;
    text-align: center;
  }
  
  h1 {
    color: #333;
  }
  
  .input-container {
    margin-bottom: 20px;
  }
  
  input {
    padding: 10px;
    width: 70%;
    border: 1px solid #ccc;
    border-radius: 4px;
    margin-right: 10px;
  }
  
  button {
    padding: 10px 20px;
    border: none;
    border-radius: 4px;
    background-color: #007bff;
    color: white;
    cursor: pointer;
  }
  
  button:hover {
    background-color: #0056b3;
  }
  
  ul {
    list-style-type: none;
    padding: 0;
  }
  
  .todo-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    border-bottom: 1px solid #ccc;
  }
  
  .todo-item:nth-child(odd) {
    background-color: #f9f9f9;
  }
  
  .remove-button {
    background-color: #dc3545;
    border: none;
    border-radius: 4px;
    color: white;
    cursor: pointer;
    padding: 5px 10px;
  }
  
  .remove-button:hover {
    background-color: #c82333;
  }
  </style>
  