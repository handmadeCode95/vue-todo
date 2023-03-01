<template>
    <v-sheet class="rounded-lg" max-width="400">
        <v-form @submit.prevent="addTodo">
            <v-text-field
                v-model="todo"
                label="Todo"
                append-inner-icon="mdi-plus"
                clearable
            />
            <v-btn type="submit" variant="outlined" class="mt-2" block>
                Save
            </v-btn>
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
        setTodos: function () {
            localStorage.setItem(
                this.TODOS_KEY,
                JSON.stringify(this.todoItems)
            );
        },
        getTodos: function () {
            const savedTodos = localStorage.getItem(this.TODOS_KEY);
            if (savedTodos !== null) {
                this.todoItems = [...JSON.parse(savedTodos)];
            }
        },
        addTodo: function () {
            this.getTodos();

            const newTodo = {
                completed: false,
                todo: this.todo,
            };
            this.todoItems.push(newTodo);

            this.setTodos();
            this.clearInput();
        },
        clearInput: function () {
            this.todo = "";
        },
    },
};
</script>
