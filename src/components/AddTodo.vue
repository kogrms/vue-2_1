<template>
    <form @submit.prevent="onSubmit">
        <input type="text" v-model="title">
        <button type="submit">New task</button>
    </form>
</template>

<script>
export default {
    data() {
        return {
            title: ''
        }
    },
    methods: {
        onSubmit () {
            console.log('Submit', this.title)
        }
    }
}
</script>

<style scoped>
form {
    display: flex;
    justify-content: space-between;
}

input {
    width: 70vw;
}
</style>