<template>
  <div v-bind:class="[class1]">
    <div v-for="(option, index) in options" :key="index">
      <label v-show="labelX" :for="name">{{ label }}:</label>
      <select class="custom-select mr-sm-2" v-model="selected" @change="updateSoF" required>
        <option disabled value="">Please select one</option>
        <option class="form-check" v-for="(value, key, index) in option" :key="index" :value="key">
          {{ value }}
        </option>
      </select>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Select',
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
      selected: this.object1.value
    }
  },
  created() {
    this.class1 = `col col-lg-${this.col}`
  },
  computed: {
    labelX: function () {
      let ifLabel = false
      if(this.label==="Source of attention") {
        ifLabel = true
        return ifLabel
      }
      return ifLabel
    }
  },
  methods: {
    updateSoF: function () {
      this.$emit('sourceOfAttention', this.name, this.selected);
    }
  }
}
</script>

<style scoped>

</style>