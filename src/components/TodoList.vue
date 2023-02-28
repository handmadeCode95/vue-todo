<template>
    <v-card max-width="300" flat>
        <v-list>
            <v-list-item
                v-for="(todo, index) in todoItems"
                :key="todo + index"
                :title="todo"
                :value="index"
            >
                <template v-slot:append>
                    <v-hover v-slot="{ isHovering, props }">
                        <v-btn
                            v-bind="props"
                            :color="
                                isHovering ? 'red-darken-4' : 'grey-lighten-1'
                            "
                            icon="mdi-minus-box"
                            variant="text"
                        ></v-btn>
                    </v-hover>
                </template>
            </v-list-item>
        </v-list>
    </v-card>
</template>

<script>
export default {
    data: () => ({
        TODOS_KEY: "todos",
        todoItems: [],
    }),
    methods: {
        getTodos: function () {
            const savedTodos = localStorage.getItem(this.TODOS_KEY);
            if (savedTodos !== null) {
                this.todoItems = [...JSON.parse(savedTodos)];
            }
        },
    },
    created: function () {
        this.getTodos();
    },
};
</script>

<style></style>
