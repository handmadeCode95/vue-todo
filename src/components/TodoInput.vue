<template>
    <v-sheet class="rounded-lg" width="304">
        <v-form @submit.prevent="addTodo">
            <v-text-field
                v-model="todo"
                label="Todo"
                append-inner-icon="mdi-plus"
                clearable
            ></v-text-field>
            <v-btn type="submit" block class="mt-2">Save</v-btn>
        </v-form>
    </v-sheet>
</template>

<script>
export default {
    data: () => ({
        TODOS_KEY: "todos",
        todo: "",
        todoItems: [],
    }),
    methods: {
        getTodos: function () {
            const savedTodos = localStorage.getItem(this.TODOS_KEY);
            if (savedTodos !== null) {
                this.todoItems = [...JSON.parse(savedTodos)];
            }
        },
        addTodo: function () {
            this.getTodos();

            this.todoItems.push(this.todo);
            localStorage.setItem(
                this.TODOS_KEY,
                JSON.stringify(this.todoItems)
            );

            this.clearInput();
        },
        clearInput: function () {
            this.todo = "";
        },
    },
};
</script>

<style></style>
