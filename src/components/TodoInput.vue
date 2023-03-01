<template>
    <v-sheet class="rounded-lg" max-width="400">
        <v-form ref="todoForm" @submit.prevent="addTodo" validate-on="submit">
            <v-text-field
                ref="todoInput"
                v-model="todo"
                label="Todo"
                :rules="todoRules"
                clearable
                append-inner-icon="mdi-plus"
            />
            <v-btn type="submit" variant="outlined" class="mt-2" block>
                Add Todo
            </v-btn>
        </v-form>
    </v-sheet>
</template>

<script>
export default {
    data: () => ({
        todo: "",
        todoRules: [(value) => !!value || "Todo is required"],
    }),
    methods: {
        addTodo: async function () {
            const { valid } = await this.$refs.todoForm.validate();

            if (!valid) return;

            this.$emit("addTodo", this.todo);
            this.$refs.todoForm.reset();
        },
    },
};
</script>
