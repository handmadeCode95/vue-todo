<template>
    <v-app>
        <todo-header />
        <v-container>
            <todo-input v-on:addTodo="addTodoItem" />
            <v-divider class="my-6" />
            <todo-list
                v-bind:todoItems="todoItems"
                v-on:removeTodo="removeTodoItem"
                v-on:toggleComplete="toggleCompleteItem"
            />
            <v-divider v-if="todoItems.length > 0" class="my-6" />
            <todo-footer v-on:allClear="allClearItems" />
        </v-container>
    </v-app>
</template>

<script>
import TodoFooter from "./components/TodoFooter.vue";
import TodoHeader from "./components/TodoHeader.vue";
import TodoInput from "./components/TodoInput.vue";
import TodoList from "./components/TodoList.vue";

export default {
    data() {
        return {
            TODOS_KEY: "todos",
            todoItems: [],
        };
    },
    methods: {
        setTodoItems() {
            localStorage.setItem(
                this.TODOS_KEY,
                JSON.stringify(this.todoItems)
            );
        },
        getTodoItems() {
            const savedTodos = localStorage.getItem(this.TODOS_KEY);
            if (savedTodos !== null) {
                this.todoItems = [...JSON.parse(savedTodos)];
            }
        },
        addTodoItem(todo) {
            const newTodo = {
                todo,
                completed: false,
            };
            this.todoItems.push(newTodo);

            this.setTodoItems();
        },
        removeTodoItem(index) {
            this.todoItems.splice(index, 1);

            this.setTodoItems();
        },
        toggleCompleteItem(index) {
            this.todoItems[index].completed = !this.todoItems[index].completed;

            this.setTodoItems();
        },
        allClearItems() {
            this.todoItems = [];
            localStorage.removeItem(this.TODOS_KEY);
        },
    },
    created() {
        this.getTodoItems();
    },
    components: { TodoHeader, TodoList, TodoInput, TodoFooter },
};
</script>
