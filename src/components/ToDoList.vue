<template>
  <div class="to-do-list">
    <div>
      <input type="text" id="new-todo" v-model="newToDo" />
      <button @click="clickAdd()">Add</button>
      <ul>
        <li v-for="todo in todolist" :key="todo.message">
          <input type="checkbox" v-model="todo.isDone">
          <span>{{ todo.text }}</span>
          <button @click="clickDelete(todo.id)">Delete</button>
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
  
  newToDo = "";

  clickAdd() {
    if (!this.newToDo) return;
    this.todolist.push({
      id: this.todolist[this.todolist.length - 1].id + 1,
      text: this.newToDo,
      isDone: false
    });
    this.newToDo = "";
  }

  clickDelete(id: number) {
    const index = this.todolist.findIndex(el => id === el.id);    
    this.todolist.splice(index, 1);
  }

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
