<template>
  <ul>
    <resource-item
      v-for="resource in injResources"
      :key="resource.id"
      :title="resource.title"
      :description="resource.description"
      :link="resource.link"
    ></resource-item>
  </ul>
</template>

<script>
import ResourceItem from './ResourceItem.vue';

export default {
  inject: ['resources'],
  data() {
    return {
      injResources: this.resources,
    };
  },
  components: {
    ResourceItem,
  },
};
</script>

<style scoped>
ul {
  list-style: none;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>
