<template>
  <div class="results">
    <ul>
      <!-- Display the text property of each result object -->
      <li v-for="(result, index) in results" :key="index">{{ result.Text?result.Text:result.Topics[0].Text  }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'SearchResults',
  props: {
    // This prop will be an array of objects with a 'text' property
    results: Array
  }
};
</script>

<style scoped>
/* Add styles for your results here */
</style>
