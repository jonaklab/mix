<template>
  <div class="container">
    <AppHeader />
    <section class="section">
      <h1 class="title">Section</h1>
      <h2 class="subtitle">
        A simple container to divide your page into <strong>sections</strong>, like the one you're currently reading
      </h2>
      <div class="field has-addons">
        <div class="control">
          <input v-model="searchedInput" class="input" type="text" placeholder="Search on youtube">
        </div>
        <div class="control">
          <button @click="search" class="button is-info">
            Search
          </button>
        </div>
      </div>
    </section>
  </div>
  <!-- ----------------------------------------------------------------- -->
  <!-- <div id="app">
    <div class="container-fluid">
      <a href="#" class="list-group-item list-group-item-action" v-for='dit in selitems'>
        <div class="card">
          <div class="row no-gutters">
            <div class="col-md-4">
              <img :src="dit.snippet.thumbnails['default'].url" class="card-img" alt="...">
            </div>
            <div class="col-md-8">
              <div class="card-body">
                <h5 class="card-title">{{dit.snippet.title}}</h5>
                <p class="card-text">This is a wider card with supporting text below as a natural lead-in to additional content. This content is a little bit longer.</p>
                <p class="card-text"><small class="text-muted">Last updated 3 mins ago</small></p>
              </div>
            </div>
          </div>
        </div>
      </a>

      <div>
        <form>
          <input class="form-control form-control-lg" type="text" placeholder="search" v-model="q">
          <button type="button" v-on:click="searchMe" class="btn btn-primary">Submit</button>
        </form>
      </div>
      <a href="#" class="list-group-item list-group-item-action" v-for='dit in items'>
        <div class="card">
          <div class="row no-gutters">
            <div class="col-md-4">
              <img :src="dit.snippet.thumbnails['default'].url" class="card-img" alt="...">
            </div>
            <div class="col-md-8">
              <div class="card-body">
                <h5 class="card-title">{{dit.snippet.title}}</h5>
                <p class="card-text">This is a wider card with supporting text below as a natural lead-in to additional content. This content is a little bit longer.
                <button type="button" v-on:click="add(dit)" class="btn btn-success">Add</button>
                </p>
                <p class="card-text"><small class="text-muted">Last updated 3 mins ago</small></p>
              </div>
            </div>
          </div>
        </div>
      </a>
    </div>
  </div> -->
</template>

<script>
import AppHeader from './components/AppHeader'
// import Sidebar from './components/Sidebar.vue'
// import ListArea from './components/ListArea.vue'
// import DetailsArea from './components/DetailsArea.vue'

import axios from 'axios'
import config from '../config.json'

export default {
  name: 'app',
  data () {
    return {
      searchedInput: null,
      items: [],
      selitems: []
    }
  },
  components: {
    AppHeader
  //  Sidebar,
  //  ListArea,
  //  DetailsArea
  },
  methods: {
    add(item) {
      this.selitems.push(item)
    },
    search() {
      let url= `https://www.googleapis.com/youtube/v3/search?q=${this.q}&part=snippet&key=${config.api_key}`
      axios.get(url).then(res => {
        console.log(res)
        this.items = res.data.items
      })
      .catch( err => {
        console.log(err)
      })
    }
  }
}
</script>

<style lang="scss">
</style>
