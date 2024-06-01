<!-- eslint-disable -->
<template>
  <div>
    <h1>Greetings, {{ username }}</h1>
    <button class="btn" @click="LogOut">LogOut</button>
    <router-link :to="{ name: 'invoices' }">
      <button class="btn">invoices</button></router-link
    >
  </div>
</template>
<!-- eslint-disable -->
<script>
export default {
  data() {
    return {
      username: window.user,
    };
  },
  methods: {
    LogOut() {
      (window.user = null), this.$router.push({ name: "home" });
    },
  },
};
</script>
