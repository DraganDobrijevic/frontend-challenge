<template>
  <div class="form container-fluid">
    <form @submit="submittedObject">
      <div class="row justify-content-center">
        <String class="form-group" :object1="firstNameObject" @input="update"/>
      </div>
      <div class="row justify-content-center">
        <String class="form-group" :object1="lastNameObject" @input="update"/>
      </div>
      <div class="row justify-content-center"> 
        <Email class="form-group" :object1="emailObject" @email="email"/>
      </div>
      <div class="row justify-content-center"> 
        <Radio class="form-group" :object1="genderObject" @gender="gender"/>
      </div>
      <div class="row justify-content-center"> 
        <Select class="form-group" :object1="sourceOfAttentionObject" @sourceOfAttention="sourceOfAttention"/>
      </div>
      <div class="row justify-content-center"> 
        <Phone class="form-group" :object1="phoneObject" @phone="phone"/>
      </div>
      <div class="row justify-content-center"> 
        <MultiString class="form-group" :object1="multiStringObject" @multiString="multiString"/>
      </div>
      <div class="row justify-content-center mt-4">
        <div class="col-6">
          <input type="submit" value="Submit" class="btn btn-outline-primary btn-block">
        </div> 
      </div>
      <hr> {{ object }} <hr>
      {{jsonObject}} 
    </form>
  </div>
</template>

<script>
import String from '@/components/String.vue'
import Email from '@/components/Email.vue'
import Radio from '@/components/Radio.vue'
import Select from '@/components/Select.vue'
import Phone from '@/components/Phone.vue'
import MultiString from '@/components/MultiString.vue'
// import axios from 'axios'
import json from '../../../resources/sample.json'

export default {
  name: 'Form',
  components: { 
    String,
    Email,
    Radio,
    Select,
    Phone,
    MultiString,
  },
  data() {
    return {
      inputObject: json,
      firstNameObject: json[0],
      lastNameObject: json[1],
      emailObject: json[2],
      genderObject: json[3],
      sourceOfAttentionObject: json[4],
      phoneObject: json[5],
      multiStringObject: json[6],
      firstNameKey: String,
      firstNameValue: String, 
      lastNameKey: String,
      lastNameValue: String, 
      emailKey: "",
      emailValue: "", 
      genderKey: "",
      genderValue: "", 
      sourceOfAttentionKey: "",
      sourceOfAttentionValue: "",
      phoneKey: "",
      phoneValue: Object,
      multiStringKey: "",
      multiStringValue: Array,
      object: Object,
      jsonObject: JSON,
    }
  },
  // created() {
  //    axios.get('https://raw.githubusercontent.com/DraganDobrijevic/frontend-challenge/master/resources/sample.json')
  //      .then(res => this.inputObject = res.data)
  //      .catch(err => console.log(err));
  // }
  methods: {
    update: function(name, value) {
      if (this.firstNameObject.name === name) {
        this.firstNameKey = name;
        this.firstNameValue = value;
      } else {
          this.lastNameKey = name;
          this.lastNameValue = value;
      } 
    },
    email: function(name, value) {
      this.emailKey = name;
      this.emailValue = value; 
    },
    gender: function(name, value) {
      this.genderKey = name;
      this.genderValue = value; 
    },
    sourceOfAttention: function(name, value) {
      this.sourceOfAttentionKey = name;
      this.sourceOfAttentionValue = value; 
    },
    phone: function(name, object) {
      this.phoneKey = name;
      this.phoneValue = object; 
    },
    multiString: function(name, value) {
      this.multiStringKey = name;
      this.multiStringValue = value; 
    },
    submittedObject: function(e) {
      e.preventDefault();
      const submittedObject = {
        [this.firstNameKey]: this.firstNameValue,
        [this.lastNameKey]: this.lastNameValue,
        [this.emailKey]: this.emailValue,
        [this.genderKey]: this.genderValue,
        [this.sourceOfAttentionKey]: this.sourceOfAttentionValue,
        [this.phoneKey]: this.phoneValue,
        [this.multiStringKey]: this.multiStringValue
      };
      this.object = submittedObject;
      console.log(this.object);
      this.jsonObject = JSON.stringify(submittedObject);
      console.log(this.jsonObject);
    }
  }
}
</script>

<style lang="sass" scoped>
  $primary-color: blue

  .home 
    color: $primary-color
  
</style>
