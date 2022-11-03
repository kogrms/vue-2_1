<template>
    <li>
        <span v-bind:class="{done: todo.completed}">
            <input type="checkbox" v-on:change="todo.completed = !todo.completed">
            <strong>{{index + 1}}</strong>
            {{todo.title | uppercase}}
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
    },
    filters: {
        uppercase(value) {
            // console.log(value)
            return value.toUpperCase()
        }
    }
}
</script>

<style scoped>
li {
    border: none;
    box-shadow: 0px 0px 8px 2px rgba(0,0,0,.2);
    border-radius: 5px;
    display: flex;
    justify-content: space-between;
    margin-bottom: 10px;
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