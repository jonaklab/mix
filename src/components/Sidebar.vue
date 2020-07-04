<template lang="pug">
  .col-2.sidebar
    ul.nav.flex-column
      li.nav-item(v-for="i in nav")
        a.nav-link(:href="i.l") {{i.t}}
</template>

<script>
export default {
  name: 'Sidebar',
  props: {
  },
  data () {
    return {
      nav: [
        {l: "/in", t: "Inbox"},
        {l: "/al", t: "All"},
        {l: "/td", t: "Today"},
        {l: "/tm", t: "Tomorrow"},
        {l: "/tw", t: "This Week"},
        {l: "/cl", t: "Calender"}
      ]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="sass" scoped>
.sidebar
  background: #333;
  color: #fff;
  position: -webkit-sticky;
  position: sticky;
  top: 4rem;
  z-index: 1000;
  height: calc(100vh - 1px);
  padding: 0;

  a
    color: white;
    &:hover
      background: #c54a4a;
</style>
