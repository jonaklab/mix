<template>
  <section class="search-results">
    <div class="box" v-for="item in searchResults" v-bind:key="item">
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
              Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean efficitur sit amet massa fringilla egestas. Nullam condimentum luctus turpis.
            </p>
          </div>
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
      // default: 'Lucas'
    }
  }
}
</script>

<style lang="scss">
  .app-header {
    margin-top: 1.5rem;
  }
</style>