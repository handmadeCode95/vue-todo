<template>
    <v-app>
        <todo-header></todo-header>
        <v-container>
            <todo-input></todo-input>
            <v-divider class="my-6"></v-divider>
            <todo-list></todo-list>
            <todo-footer></todo-footer>
        </v-container>
    </v-app>
</template>

<script>
import TodoFooter from "./components/TodoFooter.vue";
import TodoHeader from "./components/TodoHeader.vue";
import TodoInput from "./components/TodoInput.vue";
import TodoList from "./components/TodoList.vue";
export default {
    components: { TodoHeader, TodoList, TodoInput, TodoFooter },
};
</script>
