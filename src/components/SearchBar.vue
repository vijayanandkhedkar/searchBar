<template>
  <div class="search-bar">
    <input
      type="text"
      v-model="searchQuery"
      @input="submitSearch"
      @keyup.enter="submitSearch"
      placeholder="Search..."
    />
    <button @click="submitSearch">Search</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      searchQuery: '', // This holds the value of the search input
    };
  },
  methods: {
    submitSearch() {
      // Emit an event with the search query when the search is submitted
      this.$emit('search', this.searchQuery);
    },
  },
};
</script>