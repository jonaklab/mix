<template>
  <section class="search-results">
    <div class="box" v-for="(item, index) in searchResults" :key="index">
      <article class="media">
        <div class="media-left">
          <figure class="image is-128x128">
            <img :src="item.snippet.thumbnails['default'].url" alt="Image">
          </figure>
        </div>

        <div class="media-content">
          <div class="content">
            <p>
              <strong>{{item.snippet.title}}</strong>
              <br>
              {{item.snippet.channelTitle}}
            </p>
          </div>
        </div>

        <div class="media-right add-list-item">
          <button class="button is-info">Add</button>
        </div>
      </article>
    </div>
  </section>
</template>

<script>
export default {
  props: {
    searchResults: {
      type: Array,
      required: true
    }
  }
}
</script>

<style lang="scss" scoped>
  .add-list-item {
    margin-top: 5.25rem;
  }
</style>