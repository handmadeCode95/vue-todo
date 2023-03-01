<template>
    <v-sheet class="rounded-lg" max-width="400">
        <v-slide-y-transition leave-absolute group tag="v-list">
            <v-list-item
                v-for="(item, index) in todoItems"
                :key="item?.todo + index"
            >
                <template v-slot:prepend>
                    <v-list-item-action start>
                        <v-checkbox-btn
                            v-bind:model-value="item?.completed"
                            v-on:click="toggleComplete(index)"
                        ></v-checkbox-btn>
                    </v-list-item-action>
                </template>

                <v-list-item-title
                    :class="
                        item?.completed ? 'text-decoration-line-through' : ''
                    "
                >
                    {{ item?.todo }}
                </v-list-item-title>

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
        </v-slide-y-transition>
    </v-sheet>
</template>

<script>
export default {
    props: {
        todoItems: Array,
    },
    methods: {
        removeTodo(index) {
            this.$emit("removeTodo", index);
        },
        toggleComplete(index) {
            this.$emit("toggleComplete", index);
        },
    },
};
</script>
