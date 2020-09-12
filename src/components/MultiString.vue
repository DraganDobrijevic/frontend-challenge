<template>
  <div v-bind:class="[class1]">
    <label>{{ label }}:</label>
    <div v-for="i in n" :key="i">
      <div class="row justify-content-center mb-2">
        <String class="string" :object1="objectMS" :i="i" @input="addVoucher"/>
        <div v-if="i>0 && i<=n" class="col-6">
          <button type="button" class="btn btn-outline-info btn-block" @click="delVoucher($event)">Delete</button>
        </div>
        <div v-if="n==1" class="col-12 mt-2">
          <button type="button" class="btn btn-outline-info btn-block" @click="addAnotherVoucher">Add another</button>
        </div>
      </div>
      <div class="row justify-content-center">
        <div v-if="i!=1 && i==n" class="col-12">
          <button type="button" class="btn btn-outline-info btn-block" @click="addAnotherVoucher">Add another</button>
        </div>
      </div>
    </div>
  </div> 
</template>

<script>
import String from '@/components/String.vue'

export default {
  name: 'MultiString',
  props: {
    object1: Object,
  },
  components: {
    String 
  },
  data() {
    return {
      label: this.object1.label,
      name: this.object1.name,
      value: this.object1.value,
      component: this.object1.component,
      col: this.object1.col,
      n: 1,
      objectMS: Object,
      vouchers: [],
      deletedInputs: 0,
      x: 'x',
    }
  },
  created() {
    this.class1 = `col col-lg-${this.col}`

    this.objectMS = {
      label: this.label,
      name: this.name,
      value: this.value,
      component: this.component,
      col: this.col,
      deleteLabel: true,
    };
  },
  computed: {
    vouchersDone: function () {
      return this.vouchers.filter(ele => ele !== 'x' && ele !== '')
    }
  },
  watch: {
    vouchers: function () {
      this.$emit('multiString', this.name, this.vouchersDone);
    }
  },
  methods: {
    addAnotherVoucher: function() {
      this.n++;
      this.vouchers.push('x');
    },
    delVoucher: function(e) {
      const value = e.path[2].children[0].__vue__.value;
      const index = this.vouchers.indexOf(value);

      this.deletedInputs++;

      if(this.deletedInputs < this.n) {
    
        if (index > -1) {
          this.vouchers.splice(index, 1, 'x');
        }
        else {
          this.vouchers.push('x');
        }

        e.path[2].classList.add("remove");
        e.path[2].remove();
      }
      else {
        this.deletedInputs--;
      } 
    },
    addVoucher: function(name, value, e) {
      let id = e.path[0].id;
      id = id - 1;
      this.vouchers.splice(id, 1, value);
    }
  }

}
</script>

<style lang="sass" scoped>

.remove 
  display: none
  
</style>
