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

// Colors
$color-start: rgba(255, 255, 255, .6)
$color-end: rgba(12, 131, 238, .8)

$color-white: rgba(255, 255, 255, .8)

$nav-color: rgba(12, 131, 238, .8)
$nav-color-a-hover-active: rgb(44, 62, 80)

body 
  font-family: Avenir, Helvetica, Arial, sans-serif
  text-align: center
  width: 100%
  height: 100%
  overflow-x: hidden
  background: linear-gradient(to right, $color-start, $color-end)
  color: #2c3e50

#nav 
  padding: 30px
  width: 100%
  height: 80px
  background: $nav-color
  letter-spacing: 0.1rem

#nav a 
  padding: 0 1rem
  color: $color-white
  text-decoration: none
  font-weight: bold

#nav a.router-link-exact-active 
  color: $nav-color-a-hover-active

#nav a:hover
  color: $nav-color-a-hover-active 

</style>
