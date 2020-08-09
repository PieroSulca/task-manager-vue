<template>
    <div>
        <form @submit.prevent="sendLogin()">
            <input type="email" placeholder="email" name="email" v-model="user.email">
            <input type="password" placeholder="contraseña" name="password" v-model="user.password">
            <button type="submit">Ingresar</button>
        </form>
    </div>
</template>

<script>
    import axios from "axios"
    export default {
        name: 'Login',
        data: () => ({
                user: {
                    email: '',
                    password: ''
                }, 
                userName: []
        }),
        methods: {
            async sendLogin() {
                try {
                    const respuesta = await axios.post("https://academlo-todolist.herokuapp.com/login", this.user)
                    // console.log(respuesta)
                    this.userName = respuesta.data.results
                    this.$router.push('/task')
                }
                catch (error){
                    console.error(error)
                }
            },
        },
    }
</script>

<style lang="scss" scoped>

</style>