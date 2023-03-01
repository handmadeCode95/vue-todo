<template>
    <v-sheet class="rounded-lg" max-width="400">
        <v-hover v-slot="{ isHovering, props }">
            <v-btn
                variant="text"
                append-icon="mdi-trash-can-outline"
                v-on:click="allClear()"
                v-bind="props"
                :color="isHovering && 'error'"
                block
            >
                All Clear
            </v-btn>
        </v-hover>
    </v-sheet>
</template>

<script>
export default {
    data: () => ({
        TODOS_KEY: "todos",
        todoItems: [],
    }),
    methods: {
        allClear: function () {
            localStorage.removeItem(this.TODOS_KEY);
        },
    },
};
</script>
