<template>
  <div class="container">
    <form @submit.prevent="addTodo">
      <label>Title</label> <input type="text" v-model="form.title"> <br>
      <input type="submit" value="Add todo">
    </form>
  </div>
</template>
<script>
  import { baseUrl } from '../utils';

  export default {
    data: "FormTodo",
    data() {
      return {
        form: {
          completed:false,
          title:"",
          userId:1,
          id: 3
        }
      }
    },
    methods: {
      addTodo() {
        this.form.id = this.form.id + 1
        this.$emit(
          "addTodoFromChild", 
          JSON.parse( JSON.stringify(this.form))
        )
        this.form.title = ""
      }
    }
  };
</script>