<template>
  <div id="phone" v-bind:class="[class1]">
    <label>{{ label }}:</label>
    <div class="row justify-content-center">
      <Select class="form-group" :object1="object2" @sourceOfAttention="update1"/>
      <String class="form-group" :object1="object3" @input="update2"/>
      <!-- {{ phoneObject }} -->
    </div> 
  </div>
</template>

<script>
import Select from '@/components/Select.vue'
import String from '@/components/String.vue'

export default {
  name: 'Phone',
  props: {
    object1: Object,
  },
  components: {
    Select,
    String 
  },
  data() {
    return {
      label: this.object1.label,
      name: this.object1.name,
      value: this.object1.value,
      options: this.object1.options[0].ext,
      component: this.object1.component,
      col: this.object1.col,
      object2: Object,
      object3: Object,
      extName: '',
      selected: '',
      phoneName: '',
      phoneNumber: '',
      phoneObject: Object
    }
  },
  created() {
    this.class1 = `col col-lg-${this.col}`;
    this.object2 = {
      label: this.label,
      name: this.name,
      value: this.value.ext,
      options: this.options,
      component: this.component,
      col: this.col,
      ifLabel: false,
    };
    this.object3 = {
      label: this.label,
      name: this.name,
      value: this.value.phone,
      component: this.component,
      col: this.col,
      deleteLabel: true,
    };
  },
  methods: {
    update1: function(name, selected) {
      this.extName = 'ext';
      this.selected = selected;
      this.pObject()
    },
    update2: function(name, value) {
      this.phoneName = 'phone';
      this.phoneNumber = value;
      this.pObject()
    },
    pObject: function() {
      const object4 = {
        [this.extName]: this.selected,
        [this.phoneName]: this.phoneNumber
      };
      this.phoneObject = object4;
      this.$emit('phone', this.name, object4);
    },
  },
}
</script>

<style>

</style>