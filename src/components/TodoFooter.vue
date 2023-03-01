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
    methods: {
        allClear: function () {
            this.$emit("allClear");
        },
    },
};
</script>
