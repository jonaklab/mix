<template>
  <div class="container">
    <AppHeader />
    
    <section class="section">
      <div class="field has-addons has-addons-fullwidth">
        <div class="control">
            <input v-model="searchedInput" class="input is-large" type="text" placeholder="Search on youtube">
        </div>
        <div class="control">
            <button @click="search" class="button is-info is-large">Search</button>
        </div>
      </div>
    </section>

    <SearchResults :searchResults="searchResults" />
  </div>
</template>

<script>
import AppHeader from './components/AppHeader'
import SearchResults from './components/SearchResults'

import axios from 'axios'
import config from '../config.json'

export default {
  name: 'app',
  data () {
    return {
      searchedInput: null,
      searchResults: [],
      selitems: []
    }
  },
  components: {
    AppHeader,
    SearchResults
  },
  methods: {
    add(item) {
      this.selitems.push(item)
    },
    search() {
      let url= `https://www.googleapis.com/youtube/v3/search?q=${this.searchedInput}&part=snippet&key=${config.api_key}`
      axios.get(url).then(res => {
        window.console.log(res)
        this.searchResults = res.data.items
      })
      .catch( err => {
        window.console.log(err)
      })
    }
  }
}
</script>

<style lang="scss">
</style>
