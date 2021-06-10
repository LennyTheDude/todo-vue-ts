<template>
  <div class="to-do-list">
    <div>
      <ul>
        <li v-for="todo in todolist" :key="todo.message">
          <input type="checkbox" v-model="todo.isDone">
          <span>{{ todo.text }}</span>
          <!-- <button @click="deleteToDo(todolist, todo)">delete</button> -->
        </li>
      </ul>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component
export default class ToDoList extends Vue {
  @Prop() todolist!: Array<any>;
  // @Prop() delete!: Function ;

  // clickDelete(todo: any) {
  //   this.delete(todo);
  // }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
