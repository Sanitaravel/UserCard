<template>
  <div id="app">
    <UserCard v-for="user in users" :key="user.email" :user = user>
    </UserCard>
  </div>
</template>

<script>
import UserCard from './components/UserCard.vue'
import axios from 'axios'

export default {
  name: 'app',
  data(){
    return {
      users: []
    }
  },
  components: {
    UserCard
  }, 
  mounted() {
    axios.get('https://randomuser.me/api/').then((response) => {
      this.users = response.data.results
    })
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
