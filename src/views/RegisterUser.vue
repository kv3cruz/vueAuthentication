<template>
   <div>
      <form @submit.prevent="register">
         <label for="name">Name:</label>
         <input v-model="name" type="text" name="name" value="" />

         <label for="name">Email:</label>
         <input v-model="email" type="text" name="email" value="" />

         <label for="name">Password:</label>
         <input v-model="password" type="password" name="password" value="" />
         <button type="submit" name="button">Register</button>
         <ul>
            <li v-for="(error, index) in errors" :key="index" color="red">
               {{ error }}
            </li>
         </ul>
         <router-link :to="{ name: 'login' }"
            >Already have an account?</router-link
         >
      </form>
   </div>
</template>

<script>
export default {
   data() {
      return {
         name: '',
         email: '',
         password: '',
         errors: []
      }
   },
   methods: {
      register() {
         this.$store
            .dispatch('register', {
               name: this.name,
               email: this.email,
               password: this.password
            })
            .then(() => {
               this.$router.push({ name: 'dashboard' })
            })
            .catch(err => {
               console.log(err)
               this.errors = err.response.data.errors
            })
      }
   }
}
</script>

<style lang="css" scoped></style>
