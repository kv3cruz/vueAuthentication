<template>
   <div class="home">
      <h1>Welcome to the App!</h1>
      <div v-if="!loggedIn">
         to use this app you'll need to
         <router-link :to="{ name: 'login' }">Login</router-link>
         or
         <router-link :to="{ name: 'register' }">Register</router-link>
      </div>
   </div>
</template>

<script>
import { authComputed } from '../vuex/helpers'
export default {
   computed: {
      ...authComputed
   }
}
</script>
