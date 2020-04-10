<template>
  <div class="container mt-3">
    <div class="row">
      <div class="col-4">
        <Title :item="'Doing'">
        </Title>
        <hr>
        <ListTodo 
          v-for="todo in todos" :key="todo.id"
          :item="todo"
        >  
        </ListTodo>
      </div>
      <div class="col-4">
        <Title :item="'Completed'">
          <p>Todo sudah terselesaikan</p>
        </Title>
        <hr>
        <div class="card mt-3">
          <div class="card-body">
            <div class="card-title"> Jangan di hardcode </div>
            <BadgeStatus :status="'done'" />
            <BadgeStatus :status="'done'" />
          </div>
        </div>
      </div>
      <div class="col-4">
        <FormTodo @addTodoFromChild="addedTodo" ></FormTodo>
      </div>
    </div>
  </div>
</template>

<script>
  import Title from './components/Title';
  import ListTodo from './components/ListTodo';
  import FormTodo from './components/FormTodo';
  import BadgeStatus from './components/BadgeStatus';
  import { baseUrl } from './utils.js';

  export default {
    name: "App",
    data() {
      return {
        todos: []
      }
    },
    components: {
      Title,
      ListTodo,
      FormTodo,
      BadgeStatus
    },
    methods: {
      addedTodo(payload) {
        this.todos.push(payload)
        // this.getTodos()
      },
      getTodos() {
        fetch(`${baseUrl}/todos`)
          .then(response => response.json())
          .then(dataTodos => {
            this.todos = dataTodos
            console.log(this.todos)
          })
          .catch(console.log)
      }
    },
    created() {
      this.getTodos()
    },
  };
</script>