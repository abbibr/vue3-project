<template>
    <form @submit.prevent>
        <h2>Create Post</h2>
        <my-input
            placeholder="Enter title..."
            v-model:value.trim="post.title"
        />
        <my-input
            placeholder="Enter body..."
            v-model:value.trim="post.body"
        />
        <!-- <my-button @click="fetchData" style="border: 1px solid teal; color: teal;">
            Get Posts
        </my-button> -->
        <my-button type="submit" @click="createPost" style="border: 1px solid teal; color: teal;">
            Create
        </my-button>
    </form>
</template>

<script>
    import MyButton from './UI/MyButton.vue'
    import MyInput from './UI/MyInput.vue'

    export default {
        name: 'post-form',

        components: {
            MyButton, MyInput
        },

        data() {
            return {
                post: {
                    title: '',
                    body: ''
                }
            }
        },
        methods: {
            createPost() {
                this.post.id = Date.now()

                if(this.post.title.length > 0 && this.post.body.length >0){
                    this.$emit('create', this.post)

                    this.post = {
                        title: '',
                        body: ''
                    }
                }
            },
            /* fetchData() {
                this.$emit('fetchPost')
            } */
        }
    }
</script>

<style scoped>
    form{
        display: flex;
        flex-direction: column;
    }

    input{
        width: 100%;
        border: 1px solid teal;
        padding: 10px 15px;
        margin-top: 15px;
    }
</style>