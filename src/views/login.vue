<!-- eslint-disable -->
<template>
    <div class="login">
        <form class="form" @submit.prevent="login">
            <h1>Login</h1>
            <label for="username">Username</label>
            <input v-model="username" name="username" type="text" class="inbut">
            <label for="password">Password</label>
            <input v-model="password" name="password" type="password" class="inbut">
            <button class="btn">Login</button>
        </form>

    </div>
</template>
<!-- eslint-disable -->
<script>
export default {
    data() {
        return {
            username: '',
            password: ''
        }
    },
    methods: {
        login() {
            window.user = this.username
            const redirectPath = this.$route.query.redirect || '/protected'
            this.$router.push(redirectPath)
        }
    }
} 
</script>