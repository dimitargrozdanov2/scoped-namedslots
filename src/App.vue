<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Contacts>
      <div slot-scope='chocho'>
        <span> {{chocho.geroi.status}}</span>
        </div>
      <div slot name='id'>
        </div>
    </Contacts>
  </div>
</template>

<script>
import Contacts from './components/Contacts.vue'

export default {
  name: 'App',
  components: {
    Contacts
  },
  data() {
    return {
      result: {}
    }
  },

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
