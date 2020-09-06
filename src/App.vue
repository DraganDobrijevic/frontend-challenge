<template>
  <div id="app">
    <div id="nav">
      <router-link to="/input">Input</router-link>
      <router-link to="/">Form</router-link>
      <router-link to="/output">Output</router-link> 
    </div>
    <router-view/>
  </div>
</template>

<style lang="sass">

body 
  width: 100%
  overflow-x: hidden
  background: linear-gradient(to right, rgba(255, 255, 255, 0.8), rgba(12, 131, 238, .8))

#app 
  font-family: Avenir, Helvetica, Arial, sans-serif
  -webkit-font-smoothing: antialiased
  -moz-osx-font-smoothing: grayscale
  text-align: center
  color: #2c3e50
  background: linear-gradient(to right, rgba(255, 255, 255, 0.8) 0%, rgba(12, 131, 238, .8) 50%)
  height: 100%

#nav 
  padding: 30px
  width: 100%
  height: 80px
  background: rgba(12, 131, 238, .8)
  letter-spacing: 0.1rem

#nav a 
  font-weight: bold
  color: rgba(255, 255, 255, .8)
  text-decoration: none
  padding: 0 2rem

#nav a.router-link-exact-active 
  color: rgb(44, 62, 80)

#nav a:hover
  color: rgb(44, 62, 80)
  

// #nav a 
//     display: inline
//     font-size: 16px
//     font-weight: bold
//     margin-left: 20px
//     padding: 3px 5px
// 

// #nav a.router-link-exact-active  
//     /* color: #F9F9F9;  */
//     color: rgb(61, 50, 23)
//     text-decoration: none
// 

</style>
