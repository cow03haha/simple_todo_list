<template>
  <div class="todo">
    <input type="text" v-model="text" @keyup.enter="addtask">
    <button @click="addtask">Submit</button>
    <hr>
    <ol>
        <li v-for="(task, index) in todo_list" :key="task">
            {{task}} <button @click="cleartask(index)" class="remove">X</button>
        </li>
    </ol>
    <hr>
    <div v-if="todo_list.length">
        Total: {{todo_list.length}} task
        <button @click="clearall">Clear All</button>
    </div>
  </div>
</template>

<script>
export default {
    name: "Todo",
    data(){
        return{
            todo_list: [],
            text: ""
        }
    },
    methods:{
        addtask(){
            this.todo_list.push(this.text)
            this.text = ""
        },
        cleartask(index){
            this.todo_list.splice(index, 1)
        },
        clearall(){
            this.todo_list = []
        }
    }
}
</script>

<style>
    li {
        padding: 5px;
        text-align: left;
        width: 20%;
        margin: auto;
    }
</style>