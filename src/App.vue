<template>
    <div class="app">
        <post-form 
            @create="createPost"
            @fetchPost="fetchPosts"
        />
        <post-list 
            :posts="posts"
            @remove="removePost"
            v-if="!isPostsLoading"
        />
        <div v-else>
            Loading...
        </div>
    </div>
</template>

<script>
    import PostList from "./components/PostList.vue";
    import PostForm from "./components/PostForm.vue";
    import axios from 'axios'

    export default {
        name: 'App',
        components: {
            PostList, PostForm
        },

        data() {
            return {
                /* posts: [
                    {
                        id: 1,
                        title: 'JavaScript 1',
                        body: 'Description of body 1'
                    },
                    {
                        id: 2,
                        title: 'JavaScript 2',
                        body: 'Description of body 2'
                    },
                    {
                        id: 3,
                        title: 'JavaScript 3',
                        body: 'Description of body 3'
                    }
                ] */

                posts: [],
                isPostsLoading: false
            }
        },
        methods: {
            createPost(post) {
                // event.preventDefault();
                this.posts.push(post)
            },
            removePost(post) {
                this.posts = this.posts.filter(p => p.id !== post.id)
            },
            async fetchPosts() {
                this.isPostsLoading = true

                try {
                    setTimeout( async () => {
                        const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10')
                        
                        // console.log(response);
                        this.posts = response.data
                        this.isPostsLoading = false
                    }, 1500);

                } catch(e) {
                    alert('Error')
                }
            }
        },

        // saytga kirish (obnovit) bilan ma`lumotlani olib keladi (massivga)
        mounted() {
            this.fetchPosts()
        }
    }
</script>

<style>
    *{
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }

    .app{
        padding: 20px;
    }
</style>