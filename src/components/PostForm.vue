<template>
  <form @submit.prevent>
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
    <my-button
        style= "align-self: flex-end; margin-top: 15px"
        @click="createPost">Создать</my-button
    >
  </form>
</template>

<script>
import MyButton from "@/components/UI/MyButton.vue";

export default {
  components: {MyButton},
  data() {
    return {
      post: {
        title: '',
        body: ''
      }
    }
  },
  methods:{
    createPost(event) {
      this.post.id =  Date.now();
      this.$emit('create', this.post,'second param', 'third param')
      this.post ={
        title: '',
        body: ''
      }
    },
  }
}
</script>

<style  scoped>
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

.input {
  width: 100%;
  border: 1px solid teal;
  padding: 10px 15px;
  margin-top: 15px;
}



</style>