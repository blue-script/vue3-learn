<template>
  <div class="app">
    <h4>Создание поста</h4>
    <form @submit.prevent>
      <input v-bind:value="title" @input="title = $event.target.value" class="input" type="text" placeholder="Название">
      <input v-bind:value="body" @input="body = $event.target.value" class="input" type="text" placeholder="Описание">
      <button class="btn" @click="createPost">Добавить</button>
    </form>

    <div class="post" v-for="post in posts">
      <div><strong>Название</strong> {{ post.title }}</div>
      <div><strong>Описание</strong> {{ post.body }}</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      posts: [
        {id: 1, title: 'JavaScript', body: 'Описание поста'},
        {id: 2, title: 'TypeScript', body: 'Описание поста'},
        {id: 3, title: 'Vue', body: 'Описание поста'},
      ],
      title: '',
      body: '',
    }
  },
  methods: {
    createPost() {
      const newPost = {
        id: Date.now(),
        title: this.title,
        body: this.body,
      }
      this.posts.push(newPost)
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
  padding: 20px;
}

form {
  display: flex;
  flex-direction: column;
}

.btn {
  margin-top: 15px;
  align-self: flex-start;
  padding: 5px 10px;
  background: none;
  color: navy;
  border: 1px solid navy;
}

.post {
  padding: 15px;
  border: 2px solid navy;
  margin-top: 15px;
}

.input {
  width: 100%;
  padding: 5px 10px;
  margin-top: 10px;
  border: 1px solid navy;
}

</style>

<!--single style component-->