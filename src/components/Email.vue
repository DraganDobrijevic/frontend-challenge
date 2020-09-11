<template>
  <div v-bind:class="[class1]">
    <label :for="name">{{ label }}:</label>
    <input v-model="value" type="email" :id="name" :name="name" autocomplete="off" class="form-control text-center" required @input="updateEmail($event.target.value)">
  </div>
</template>

<script>
export default {
  name: 'Email',
  props: {
    object1: Object,
  },
  data() {
    return {
      label: this.object1.label,
      name: this.object1.name,
      value: this.object1.value,
      component: this.object1.component,
      col: this.object1.col,
      class1: "",
    }
  },
  created() {
    this.class1 = `col col-lg-${this.col}`
  },
  methods: {
    updateEmail: function (value) {
      this.$emit('email', this.name, value);
    }
  }
}
</script>

<style scoped>

</style>