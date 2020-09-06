<template class="container-fluid">
  <div class="form">
    <form @submit="submittedObject" class="form1">
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
          <input type="submit" value="Submit" class="btn-block btn2 btn2--blue btn2--animated">
          <!-- <input type="submit" value="Submit" class="btn btn-outline-primary btn-block btn2 btn2--green btn2--animated"> -->
        </div> 
      </div>
      <!-- <hr> {{ object }} <hr>
      {{jsonObject}}  -->
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

      this.$router.push({ path: '/output', query: submittedObject})
    }
  }
}
</script>

<style lang="sass" scoped>
  $primary-color: blue
  // Colors
  $color-primary: rgba(69, 83, 211, .5)
  $color-primary-light:  rgba(18, 241, 211, 0.8)
  $color-primary-dark: rgba(68, 82, 211, 0.8)

  $color-white: #fff
  $color-black: #000

  // Font
  $default-font-size: 1rem

  .form 
    position: absolute
    width: 100%
    padding: 4rem
    transform: skewY(-4.5deg)
    background: linear-gradient(to right, rgba(12, 131, 238, .8), rgba(255, 255, 255, .6))

  form
    transform: skewY(4.5deg)

  .btn2 
    &,
    &:link,
    &:visited 
      text-decoration: none
      // padding: .8rem 4rem
      display: inline-block
      transition: all .6s ease-in-out 

      padding: .375rem .75rem
      line-height: 1.5
      position: relative
      font-size: $default-font-size
      cursor: pointer
    
    &:hover 
      transform: translateY(-3px)
      color: $color-white
      border: 1px solid transparent
      border-radius: 7rem  
      box-shadow: 0 1rem 2rem rgba($color-black, .2)
      background: rgba(12, 131, 238, .8)

      &::after 
        transform: scaleX(1.4) scaleY(1.6)
        opacity: 0
        
    &:active,
    &:focus 
      outline: none
      transform: translateY(-1px)
      box-shadow: 0 .5rem 1rem rgba($color-black, .2)
        
    &--blue 
      color: #005CC8
      background-color: transparent
      border: 1px solid #005CC8
      border-radius: .25rem 

    &--animated 
      animation: moveInBottom 1s ease-in 
      animation-fill-mode: backwards

  @keyframes moveInBottom 
    0% 
      opacity: 0
      transform: translateY(1rem)
    
    100% 
      opacity: 1
      transform: translate(0)      
    
</style>
