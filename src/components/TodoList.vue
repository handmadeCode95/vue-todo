<template>
    <v-sheet class="rounded-lg" max-width="400">
        <v-list>
            <v-list-item
                v-for="(item, index) in todoItems"
                :key="item?.todo + index"
                :title="item?.todo"
                :value="index"
                v-on:click="toggleComplete(index)"
            >
                <template v-slot:prepend>
                    <v-list-item-action start>
                        <v-checkbox-btn
                            v-bind:model-value="item?.completed"
                        ></v-checkbox-btn>
                    </v-list-item-action>
                </template>
                <template v-slot:append>
                    <v-hover v-slot="{ isHovering, props }">
                        <v-btn
                            v-on:click="removeTodo(index)"
                            v-bind="props"
                            :color="isHovering ? 'error' : 'grey-lighten-1'"
                            icon="mdi-minus-box"
                            variant="text"
                        />
                    </v-hover>
                </template>
            </v-list-item>
        </v-list>
    </v-sheet>
</template>

<script>
export default {
    props: {
        todoItems: Array,
    },
    methods: {
        removeTodo: function (index) {
            this.$emit("removeTodo", index);
        },
        toggleComplete: function (index) {
            this.$emit("toggleComplete", index);
        },
    },
};
</script>
