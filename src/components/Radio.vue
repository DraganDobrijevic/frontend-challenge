<template>
  <div v-bind:class="[class1]">
    <label :for="name">{{ label }}:</label>
      <div v-for="(option, index) in options" :key="index">
        <div class="form-check form-check-inline" v-for="(value, key, index) in option" :key="index">
          <input class="form-check-input" type="radio" :id="index" :name="name" :value="key" v-model="picked" @change="updateRadio">
          <label class="form-check-label" :for="name">{{ value }}</label>
        </div>
      </div>
  </div>
</template>

<script>
export default {
  name: 'Radio',
  props: {
    object1: Object,
  },
  data() {
    return {
      label: this.object1.label,
      name: this.object1.name,
      value: this.object1.value,
      component: this.object1.component,
      options: this.object1.options,
      col: this.object1.col,
      class1: "",
      picked: "",
    }
  },
  created() {
    this.class1 = `col col-${this.col}`
  },
  methods: {
    updateRadio: function () {
      this.$emit('gender', this.name, this.picked);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
