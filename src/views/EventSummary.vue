<template>
  <div>
    <div :class="{truncate: !expanded}">{{event.summary}}</div>
    <a v-if="!expanded" @click="expanded=true">view more</a>
    <a v-else @click="expanded=false">show less</a>
  </div>
</template>
<script>
export default {
  name: 'EventSummary',
  props: {
    event: {}
  },
  data () {
    return {
      expanded: false
    }
  }
}
</script>
<style scoped>
  table, th, td {
    border: 1px solid black;
  }
  .truncate {
    width: 350px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }
  a {
    cursor: pointer;
    color: cadetblue;
  }
</style>
