<template>
  <div id="app">
      <UserProfile/>
  </div>
</template>
<script>
import UserProfile from './components/UserProfile';
export default {
  name: 'App',
  components:{
    UserProfile
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin-top: 60px;
}
</style>
