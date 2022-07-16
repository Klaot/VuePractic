<template>
<div class="app">
    <form @submit.prevent>
        <h1>Создание поста:</h1>
        <input
         v-bind:value="title"
         class="input" type="text"
         placeholder="Название поста"
         @input="title = $event.target.value">
        <input
         v-bind:value="body"
         class="input" type="text"
         placeholder="Пост"
         @input="body = $event.target.value">
        <button @click="createPost">Добавить</button>
    </form>
    <div class="post" v-for="post in posts">
        <div><strong>Название: </strong>{{post.title}}</div>
        <div><strong>Описание: </strong>{{post.body}}</div>
   </div>
</div>
   
</template>

<script>

export default {
    data() {
        return {
            posts: [
                {id: 1, title:"JavaScript", body: 'Универсальный язык програмирования 1'},
                {id: 2, title:"JavaScript", body: 'Универсальный язык програмирования 2'},
                {id: 3, title:"JavaScript", body: 'Универсальный язык програмирования 3'},
            ],
            title: '',
            body: ''
        }   
    },
    methods: {
        createPost() {
            const newPost = {
                id: Date.now(),
                title: this.title,
                body: this.body
            }
            this.posts.push(newPost)
            this.title = '',
            this.body = ''
        },
        
    }
}

    
    

</script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

.app {
    padding: 10px;
}

.post {
    padding: 15px;
    border: 1px solid rgb(87, 77, 233);
    margin-top: 15px;
}

.input {
    width: 100%;
    border: 1px solid rgb(87, 77, 233);
    padding: 10px 15px;
    margin-top: 15px;
}

button {
    margin-top: 10px;
    padding: 10px;
}
</style>