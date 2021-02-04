<template>
  <ul>
    <!-- <li v-for="resource in storedResources">
          <p></p>
      </li> -->
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
          description: 'The officcial Vue.js documentaion',
          link: 'https://vuejs.org'
        },
        {
          id: 'google',
          title: 'Google',
          description: 'Learn to google...',
          link: 'https://google.com'
        }
      ]
    };
  }
};
</script>

<style lang="scss" scoped></style>
