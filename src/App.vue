<template>
  <div class="wrapper">
    <!-- header -->
    <div class="wrapper-content">
      <div class="view">
        <div class="container">
          <list-form @onSubmit="addTweet" />
          <list :items="items" />
        </div>
      </div>
    </div>
    <!-- foter -->
  </div>
</template>
<script>
import List from '@/components/List.vue';
import ListForm from '@/components/ListForm.vue';
import { ref } from 'vue';

export default {
  components: { List, ListForm },
  setup() {
    const items = ref([
      {
        id: 1,
        avatar: `https://avatars.dicebear.com/api/male/1.svg`,
        date: new Date(Date.now()).toLocaleString(),
        text: 'This is good tweet',
        likes: 11,
      },
      {
        id: 2,
        avatar: `https://avatars.dicebear.com/api/male/2.svg`,
        date: new Date(Date.now()).toLocaleString(),
        text: 'Many p-s likes do it',
        likes: 4,
      },
    ]);

    const addTweet = data => items.value.push(data);

    return {
      items,
      addTweet,
    };
  },
};
</script>
