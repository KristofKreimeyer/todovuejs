<template>
    <div class="wrapper">
        <div class="form">
            <form @submit.prevent="addTodo">
                <input type="text" placeholder="Eintrag hinzufügen" class="form-control" v-model="todoTitle">

            </form>
        </div>
        <ul class="list-group">
            <transition-group enter-active-class="animated bounceIn" leave-active-class="animated bounceOut">
                <Todo v-for="(data,index) in todos" :key="index" :title="'#' + data.title" :done="data.done" :deleteTodo="(event) => deleteTodo(index)"/>
            </transition-group>
        </ul>
    </div>

</template>

<script>
    import Todo from "./Todo";
    import axios from "axios";

	export default {
		name: "TodoList",
        components: {
			Todo
        },
		data: () => ({
			todos: [
				{title: '  Task 1 ', done: false},
				{title: '  Task 2 ', done: false},
			],
            todoTitle: ""
		}),
        methods: {
			addTodo() {
                axios.put('http://localhost:3000/todos', {title: this.todoTitle, done: false}).then((response) => {
                    if(response.data.ok) {
                        this.refresh();
                    }
                })
				/*this.todos.push({
                    title: this.todoTitle,
                    done: false
                })*/
                this.todoTitle = ""
            },
            deleteTodo(index) {
                axios.delete(`http://localhost:3000/todos/${this.todos[index].id}`).then((response) => {
                    if(response.data.ok) {
                        this.refresh();
                    }
                })
				//this.todos.splice(index, 1)
            },
            refresh() {
                axios.get('http://localhost:3000/todos/').then((response) => {
                    this.todos = response.data.todos;
                })
            }
        },
        mounted() {
			this.refresh()
        }
	}
</script>

<style scoped>

</style>
