<template>
    <li>
        <span v-bind:class="{done: todo.completed}">
            <input type="checkbox" v-on:change="todo.completed = !todo.completed">
            <strong>{{index + 1}}</strong>
            {{todo.title}}
        </span>
        <button class="btn-rm" v-on:click="$emit('rm-todo', todo.id)">
            &times;
        </button>
    </li>
</template>

<script>
export default {
    props: {
        todo: {
            type: Object,
            required: true
        },
        index: Number
    }
}
</script>

<style scoped>
li {
    border: 1px solid #a6a6a6;
    border-radius: 5px;
    display: flex;
    justify-content: space-between;
    margin-bottom: 5px;
    padding: 10px;
}

input {
    margin: 0;
    padding: 0;
    margin-right: 10px;
}

.btn-rm {
    border: none;
    border-radius: 10px;
    color: white;
    background-color: red;
    height: 19px;
    width: 19px;
}

.done {
    text-decoration: line-through;
}
</style>