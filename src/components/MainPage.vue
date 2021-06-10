<template>
  <div class="hello">
    <ToDoList :todolist="list" />
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import ToDoList from '@/components/ToDoList.vue'
@Component({
  components: {
    ToDoList,
  },
})
export default class MainPage extends Vue {
  @Prop() private msg!: string;
  firstName = "Lenny";
  lastName = "The Dude";
  
  list = [
    {
      text: "Play Africa by Toto",
      isDone: false
    },
    {
      text: "Run to the store",
      isDone: false
    },
    {
      text: "Get some Gin & Juice",
      isDone: true
    },
    {
      text: "Join the lobby",
      isDone: false
    },
  ];
  
  counter = 0;

  get fullName() { return this.firstName + " " + this.lastName }

  incrementCounter() {
    this.counter++
  }

  decrementCounter() {
    this.counter--
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
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
