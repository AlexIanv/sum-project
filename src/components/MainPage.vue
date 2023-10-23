<template>
    <div>
        <div v-if="isAuthenticated">
            <div>Привет, <b>{{ username }}!</b></div>
            <button @click="logout">Выйти</button>
        </div>
        <div v-else>
            <label>Ваше имя: </label>
            <input v-model="username" @keyup.enter="login">
            <button @click="login">Войти</button>
        </div>
    </div>
</template>

<script>

export default {
    name: 'HomePage',
    data() {
        return {
            isAuthenticated: false,
            username: ''
        }
    },
    methods: {
        login() {
            if (this.username !== '') {
                console.log('You entered as', this.username)
                this.isAuthenticated = true
                localStorage.setItem('isAuthenticated', true)
                localStorage.setItem('username', this.username)
                this.$router.push[{
                    name: 'Chat',
                    query: { username: this.username }
                }]
            } else {
                console.log('Укажите Ваше имя, пожалуйста!')
            }
        },
        logout() {
            this.isAuthenticated = false
            this.username = ''
            localStorage.removeItem('isAthenticated')
            localStorage.removeItem('username')
        }
    },
    created() {
        if (localStorage.getItem('isAuthenticated')) {
            this.isAuthenticated = true
            this.username = localStorage.getItem('username')
        }
    }
}

</script>

<style scoped>
div {
    padding: 20px;
    font-size: 25px;
    color: #ccc;
}

label {
    margin: 1px;
}

button {
    margin-left: 10px;
    border-radius: 5px;
}
input{
    border-radius: 5px;
}
</style>