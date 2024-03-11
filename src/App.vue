<script setup>
import {ref} from 'vue';
import Profile from './components/Profile.vue';
const isOpen = ref(true)
</script>

<template>
 <div>
   <Profile v-if="isOpen"/>
 </div>
</template>

<style>
*{
  box-sizing: border-box;
  margin: 1rem;
  padding: 0;
}
body{
  background: #815132;
  color: #31ff31;
}
#app{
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  min-height: 100vh;
  max-width: 40rem;
  margin: 0 auto;
  text-align: center;
}

a{
  color: #31ff31;
}
</style>