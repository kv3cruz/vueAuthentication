<template>
   <div>
      <form @submit.prevent="register">
         <label for="name">Name:</label>
         <input v-model="name" type="text" name="name" value="" />

         <label for="name">Email:</label>
         <input v-model="email" type="text" name="email" value="" />

         <label for="name">Password:</label>
         <input v-model="password" type="text" name="password" value="" />
         <button type="submit" name="button">Register</button>
      </form>
   </div>
</template>

<script>
export default {
   data() {
      return {
         name: '',
         email: '',
         password: ''
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
      }
   }
}
</script>

<style lang="css" scoped></style>
