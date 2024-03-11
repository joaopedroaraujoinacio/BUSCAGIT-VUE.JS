<script setup>
defineProps(['login', 'name', 'company','bio', 'avatar_url'])
</script>
<template>
 <div> 
  <img :src="avatar_url">
  <strong>@{{login}}</strong>
  <h2>{{name}}</h2>
  <h3>{{company}}</h3>
  <span>{{bio}}</span>
</div>
</template>

<style scoped>
img{
  display: block;
  border-radius: 999px;
  border: 1px solid #31ff31;
  margin: 1rem auto;
  width: 8rem;
  height: 8rem;
}

h1, h2{
  color: #ffffff;
  margin: 1.5rem auto .25rem;  
}
h3{
  margin: 1rem auto .25rem;
}
span{
  display: block;
  margin: 1rem auto;  
}
</style>