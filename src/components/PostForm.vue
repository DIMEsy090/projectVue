<template>
  <form @submit.prevent>
    <h4>Создание поста</h4>
    <my-input v-model="post.title" type="text" placeholder="Название" />
    <my-input v-model="post.body" type="text" placeholder="Описание" />
    <my-button
      style="align-self: flex-end; margin-top: 15px"
      @click="createPost"
      >Создать</my-button
    >
  </form>
</template>

<script>
import MyButton from "@/components/UI/MyButton.vue";
export default {
  components: { MyButton },
  data() {
    return {
      post: {
        title: "",
        body: "",
      },
    };
  },
  methods: {
    createPost(event) {
      this.post.id = Date.now();
      this.$emit("create", this.post, "second param", "third param");
      this.post = {
        title: "",
        body: "",
      };
    },
  },
};
</script>

<style scoped>
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
</style>
