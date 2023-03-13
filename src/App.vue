<template>
  <ul>
    <li v-for="resource in storedResources" :key="resource.id">
      {{ resource }}
    </li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'The official Vue.js documentation',
          link: 'https://vuejs.org',
        },
        {
          id: 'google',
          title: 'Google',
          description: 'You need to know how to google stuff!',
          link: 'https://google.com',
        },
      ],
    };
  },
};
</script>
