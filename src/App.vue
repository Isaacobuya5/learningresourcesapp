<template>
<stored-resources :resources="storedResources"></stored-resources>
</template>

<script>
import StoredResources from "./components/learning-resources/StoredResources.vue"
export default {
  data() {
    return {
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'The Official VueJS documentation.',
          link: 'https://vuejs.org'
        },
        {
          id: 'google',
          title: 'Google Reference',
          description: 'The Google site searches reference.',
          link: 'https://google.com'
        }
      ]
    };
  },
  components: {
      StoredResources,
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');
* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}
</style>
