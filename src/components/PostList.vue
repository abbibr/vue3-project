<template>
    <div v-if="posts.length > 0">
        <div v-for="post in posts" :key="post in posts">
            <post-item :post="post" @remove="$emit('remove', post)" />
        </div>
    </div>
    <div v-else>
        <h3 style="color: red;">There are not any posts!</h3>
    </div>
</template>

<script>
    import PostItem from '../components/PostItem.vue'

    export default {
        name: 'post-list',
        components: {
            PostItem
        },

        props: {
            posts: {
                type: Array,
                required: true
            }
        }
    }
</script>

<style scoped>
</style>