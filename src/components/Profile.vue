<script setup>
import { reactive, ref, computed, onMounted, onUpdated, onUnmounted } from 'vue';
import UserInfo from './UserInfo.vue';
import Repository from './Repository.vue';
import Form from './Form.vue';

const searchInput = ref('');

const state = reactive({
  name: '',
  login: '',
  bio: '',
  company:'',
  avatar_url:'',
  repos: []
  
});

async function fetchGithubUser(username){
      const res = await fetch(`https://api.github.com/users/${username}`);
      const {login, name, bio, company, avatar_url} = await res.json();

      state.login = login
      state.name = name
      state.bio = bio
      state.company = company
      state.avatar_url = avatar_url

      fetchUserRepositoreis(login);
   }

  async function fetchUserRepositoreis(username){
    const res = await fetch(`https://api.github.com/users/${username}/repos`);
    const repos = await res.json();

    state.repos = repos

  }
  const reposCountMessage = computed(()=>{
   return state.repos.length > 0 
    ? `${state.name} possui ${state.repos.length} repositórios públicos`
    : `${state.name} não possui nenhum repositório públicos`;
  });

  onMounted(()=>{
    console.log('O componente foi montado.')
  });

  onUpdated(()=>{
    console.log('atualizado.')
  });

  onUnmounted(()=>{
    console.log('o componente foi desmontado.')
  });
</script>

<template>    
  <main>
    <h1>GitHub Buscador</h1>
    <Form @form-submit="fetchGithubUser"/>
    <UserInfo v-if="state.login !== ''"  
      :login="state.login" :name="state.name" :company="state.company" :bio="state.bio" :avatar_url="state.avatar_url"/>
  <div v-if="state.repos.length > 0">
    <h2>{{ reposCountMessage }}</h2>
    <article >
      <Repository v-for="repo of state.repos" :full_name="repo.full_name" :description="repo.description" :html_url="repo.html_url"/>
    </article>
  </div>
  </main>
</template>