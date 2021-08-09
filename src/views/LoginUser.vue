<template>
   <div>
      <form @submit.prevent="login">
         <label for="name">Email:</label>
         <input v-model="email" type="text" name="email" value="" />

         <label for="name">Password:</label>
         <input v-model="password" type="password" name="password" value="" />
         <button type="submit" name="button">Login</button>

         <router-link :to="{ name: 'register' }"
            >Don't have an account? Register</router-link
         >
      </form>
   </div>
</template>

<script>
export default {
   data() {
      return {
         email: '',
         password: ''
      }
   },
   methods: {
      login() {
         this.$store
            .dispatch('login', {
               email: this.email,
               password: this.password
            })
            .then(() => {
               this.$router.push({ name: 'dashboard' })
            })
      }
   }
}
</script>

<style lang="css" scoped></style>
