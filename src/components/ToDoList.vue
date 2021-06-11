<template>
  <div class="to-do-list">
    <div>
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
