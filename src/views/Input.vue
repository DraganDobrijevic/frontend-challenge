<template>
  <div class="input">
      <h3>sample.json</h3>
      [
      <div v-for="(object, index) in myJson" v-bind:key="index">
          <br>
          {{ object }},
      </div>
      <br>
      ]
  </div>
</template>

<script>
import json from '../../../resources/sample.json'

export default {
    data() {
        return {
            myJson: json,
        }
    }
}
</script>

<style lang="sass" scoped>

.input
    position: absolute
    // height: 100%
    overflow-y: auto
    width: 100%
    padding: 10rem 1rem

</style>