<template>
    <div class="post">
        <div class="block_1">
            <div><strong>Title: </strong>{{ post.title }}</div>
            <div><strong>Body: </strong>{{ post.body }}</div>
        </div>

        <div class="block_2">
            <my-button @click="$emit('remove', post)" style="border: 1px solid red; color: red;">
                Delete
            </my-button>
        </div>
    </div>
</template>

<script>
    import MyButton from './UI/MyButton.vue'

    export default {
        name: 'post-item',

        components: {
            MyButton
        },

        props: {
            post: {
                type: Array,
                required: true
            }
        }
    }
</script>

<style scoped>
    .post{
        padding: 15px;
        border: 1px solid teal;
        margin-top: 15px;
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
    .block_2{
        margin-bottom: 5px;
    }
</style>