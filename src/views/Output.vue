<template>
  <div class="output">
    <h3>request.json</h3>
    <p>{{ data }}</p>
  </div>
</template>

<script>

export default {
  props: {
    submittedObject: Object
  },
    data() {
         return {
           data: this.$route.query
         }
    },
}
</script>

<style lang="sass" scoped>

  .output
    position: absolute
    // height: 100%
    overflow-y: auto
    width: 100%
    padding: 10rem 1rem

</style>
