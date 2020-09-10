<template>
  <div v-bind:class="[class1]">
    <label v-show="ifLabel" :for="name">{{ label }}:</label> 
    <input v-model.lazy="value" :type="type" :id="i" :name="name" autocomplete="off" class="form-control text-center" required @change="updateValue($event)">
  </div>
</template>

<script>
export default {
  name: 'String',
  props: {
    object1: Object,
    i: Number
  },
  data() {
    return {
      label: this.object1.label,
      name: this.object1.name,
      value: this.object1.value,
      component: this.object1.component,
      col: this.object1.col,
      class1: "",
      ifLabel: true,
      type: ""
    }
  },
  created() {
    this.class1 = `col col-lg-${this.col}`

    if(this.object1.deleteLabel) {
      this.ifLabel = false
    }

    if(this.object1.name === 'phone') {
      this.type = 'tel';
    }
    else {
      this.type = 'text';
    }
  },
  methods: {
    updateValue: function (e) {
      this.$emit('input', this.name, this.value, e);
    }
  }
}
</script>

<style lang="sass" scoped>

</style>
