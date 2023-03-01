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
        todo: "",
    }),
    methods: {
        addTodo: function () {
            this.$emit("addTodo", this.todo);
            this.clearInput();
        },
        clearInput: function () {
            this.todo = "";
        },
    },
};
</script>
