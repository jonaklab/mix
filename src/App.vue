<template lang="pug">
  #app
    .container-fluid 
      .row  
        div.col-12.text-center
          h1
            <b>You</b>
            <span class="badge badge-danger">Mix</span>
      .row 
        div.col-4
          <div class="list-group list-group-flush">
            a(href="#" class="list-group-item list-group-item-action" v-for='dit in selitems')
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
          </div>
        div.col-8
          div 
            form
              <input class="form-control form-control-lg" type="text" placeholder="search" v-model="q">
              <button type="button" v-on:click="searchMe" class="btn btn-primary">Submit</button>
          div
            <div class="list-group list-group-flush">
              a(href="#" class="list-group-item list-group-item-action" v-for='dit in items')
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
            </div>
</template>


<style src="./assets/sass/style.scss" lang="scss"></style>

<script>
// import Sidebar from './components/Sidebar.vue'
// import ListArea from './components/ListArea.vue'
// import DetailsArea from './components/DetailsArea.vue'

import axios from 'axios'
import config from '../config.json'

export default {
  name: 'app',
  data () {
    return {
      q: '',
      items: [],
      selitems: []
    }
  },
  components: {
  //  Sidebar,
  //  ListArea,
  //  DetailsArea
  },
  methods: {
    add(item) {
      player.cueVideoById(item.id.videoId,0)
      player.playVideo()
      this.selitems.push(item)
      player.seekTo(0)
    },
    searchMe() {
      let url= `https://www.googleapis.com/youtube/v3/search?q=${this.q}&part=snippet&key=${config.api_key}`
      axios.get(url).then(res => {
        console.log(res)
        this.items = res.data.items
      }).catch(console.log)
    }
  }
}
</script>
