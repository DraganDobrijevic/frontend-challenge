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

<style>

</style>