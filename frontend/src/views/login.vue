<template>
  <div>
  <h1>login</h1>

  <form class="login container" @submit.prevent="connexion">
    <div class="center box-login">
      <input required v-model="login" type="email" placeholder="Identifiant" style="width:80%; font-size:20px; margin-bottom:30px;">
      <br>
      <input required v-model="password" type="password" placeholder="Mot de passe" style="width:80%; font-size:20px; margin-bottom:80px;">
      <br>
      <button type="submit" class="btn btn-dark">Me connecter</button>
    </div>
  </form>
  </div>
</template>

<script>
import authService from "@/services/auth_service";

export default {
name: "login",
  data() {
    return {
      login: '',
      password: '',
    }
  },
  methods: {
    connexion: function () {
      console.log("connexion")
      const _authService = new authService()
      _authService.login(this.login, this.password).then( (response) => {
        if(response.status == 200){
          localStorage.setItem('user',  JSON.stringify(response.data))
          localStorage.setItem('token',  response.data.token)

          this.$router.replace('/')
          location.reload()

        }
      }).catch(function (error) {
        console.log(error)
      });
    }
  },
}
</script>

<style scoped>

</style>
