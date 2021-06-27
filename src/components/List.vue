<template>
  <div>
    <select class="sorted" v-model="sortBy">
      <option value="date">by Date</option>
      <option value="likes">by Likes</option>
    </select>
    <ul class="tweets__wrapper">
      <list-item v-for="item in sorteredItems" :key="item.id" :item="item" />
    </ul>
  </div>
</template>
<script>
import ListItem from './ListItem.vue';
import { ref, computed } from 'vue';
export default {
  components: { ListItem },
  name: 'List',
  props: {
    items: {
      type: Array,
      reqired: true,
    },
  },
  setup({ items }) {
    const sortBy = ref('date');

    const sorteredItems = computed(() => {
      return items.sort((a, b) => {
        if (a[sortBy.value] < b[sortBy.value]) return 1;
        if (a[sortBy.value] > b[sortBy.value]) return -1;
      });
    });

    return {
      sortBy,
      sorteredItems,
    };
  },
};
</script>

<style lang="scss" scoped>
.sorted {
  display: block;
  margin: 0 auto;
  margin-bottom: 15px;
}
</style>
