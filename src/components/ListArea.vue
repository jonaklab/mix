<template lang="pug">
  .col-5.ml-sm-auto.list-area
    h2.title
      | Inbox
    .create-new
      input.form-control
    .list-all 
      b-list-group.parent
        b-list-group-item(v-for="item in listItems")
          a(v-b-toggle="`accr`+item" href="#") {{item}}
          b-collapse(:id="`accr`+item")
            b-list-group.child
              b-list-group-item hello
              b-list-group-item hi
              b-list-group-item yoo
</template>

<script>
export default {
  name: 'ListArea',
  props: {
  },
  data () {
    return {
      listItems: [
        "Overdue",
        "Today",
        "No Date"
      ]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="sass" scoped>
.list-area 
  background: #fff
.parent 
  > .list-group-item 
    border-left: 0
    border-right: 0
    &::first-child 
      border-top: 0
.child 
  > .list-group-item 
    border-left: 0
    border-right: 0
    &:first-child 
      border-top: 0
    &:last-child 
      border-bottom: 0
</style>
