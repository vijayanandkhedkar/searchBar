<template>
  <div id="app">
    <SearchBar @search="fetchResults" />
    <SearchResults :searchQuery="searchQuery" :results="results" />
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar.vue';
import SearchResults from './components/SearchResults.vue';


export default {
  name: 'App',
  components: {
    SearchBar,
    SearchResults
  },
  data() {
    return {
      searchQuery: '',
      results: []
    };
  },
  methods: {
    async fetchResults(query) {
      this.searchQuery = query;
      try {
        console.log(query);
        const response = await axios.get(`https://api.duckduckgo.com/`, {
          params: { q: query, format: 'json' }
        });
        //console.log(response.data.RelatedTopics);
        this.results = this.processResults(response.data.RelatedTopics);
      } catch (error) {
        console.error('Error fetching results:', error);
        this.results = [];
      }
    },
    processResults(data) {
      // Process the data from DuckDuckGo to match your Results component format
      // This is a placeholder, adjust it according to the actual data structure
      console.log(data);
      return data;
    }
  }
};
</script>