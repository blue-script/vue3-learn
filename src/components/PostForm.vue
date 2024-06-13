<template>
  <form @submit.prevent="createPost">
    <h4>Создание поста</h4>
    <input
        v-model="post.title"
        class="input"
        type="text"
        placeholder="Название"
    >
    <input
        v-model="post.body"
        class="input"
        type="text"
        placeholder="Описание"
    >
    <button class="btn" type="submit">Добавить</button>
  </form>

</template>

<script>
export default {
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
      this.$emit('create', { ...this.post });
      this.post = {
        title: '',
        body: ''
      }
    }
  }
}
</script>

<style scoped>
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


.input {
  width: 100%;
  padding: 5px 10px;
  margin-top: 10px;
  border: 1px solid navy;
}
</style>