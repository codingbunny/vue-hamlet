<template>
  <div class="navbar">
    <router-link :to="{ name: 'index' }" tag="li">Home</router-link>
    <router-link :to="{ name: 'admin' }" tag="li">Admin</router-link>
    <router-link :to="{ name: 'login' }" tag="li" v-if="!$auth.ready()">Login</router-link>
    <li v-else @click="logout">Logout</li>
  </div>
</template>

<script>
  export default {
    methods: {
      logout() {
        this.$auth.logout().then(() => {
          console.log('>>> logout');
          this.$router.push({ name: 'index' });
        });
      },
    },
  };
</script>

<style scoped>
  .navbar li {
    cursor: pointer;
    display: inline;
    margin: 0 0 20px 20px;
  }
</style>
