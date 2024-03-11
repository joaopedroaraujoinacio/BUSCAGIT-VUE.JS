<script setup>
import{ref} from 'vue';
  const emit = defineEmits(['formSubmit'])
  const searchInput = ref('')

  function handleSubmit(ev){
    ev.preventDefault()
    emit('formSubmit', searchInput.value)
  }
</script>

<template>
  <form @submit="handleSubmit" >
      <input type="text" v-model="searchInput">
      <button >BUSCAR USUÁRIO</button>
  </form> 
</template>

<style scoped>

input, button{
  max-width: 20rem;
  padding: .5rem;
}
input{
  background: #1c1a1d;
  border: 1px solid #31ff31;
  border-radius: .25rem;
  color: #ffffff;
  margin: 1rem 1rem 1rem 0;
}
button{
  background: #6e3712;
  border: 2px solid #31ff31;
  border-radius: 1rem;
  color: #ffffff;
  font-size: 1rem;
  font-weight: 700;
  text-transform: uppercase;
}
button:hover{
  cursor: pointer;
  filter: brightness(.95);
}

</style>