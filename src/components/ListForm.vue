<template>
  <form @submit.prevent="onSubmit">
    <textarea v-model="body" required placeholder="Type tweet here" />
    <br />
    <button class="btn btnTweet">Post Tweet</button>
  </form>
</template>
<script>
import { ref } from 'vue';
export default {
  name: 'ListForm',

  setup(_, { emit }) {
    const body = ref('');

    const onSubmit = () => {
      emit('onSubmit', {
        id: Date.now(),
        avatar: `https://avatars.dicebear.com/api/male/${Date.now()}.svg`,
        date: new Date(Date.now()).toLocaleString(),
        text: body.value,
        likes: 0,
      });
      body.value = '';
    };

    return {
      body,
      onSubmit,
    };
  },
};
</script>
