<template>
  <div>
    <h1>register</h1>

    <form class="login" @submit.prevent="inscription">
      <div class="center box-login">
        <h1 style="color: #333; margin-bottom:80px;">Bienvenue</h1>
        <input required v-model="username" type="text" placeholder="Username" style="width:80%; font-size:20px; margin-bottom:80px;">
        <br>
        <input required v-model="email" type="email" placeholder="E-mail" style="width:80%; font-size:20px; margin-bottom:30px;">
        <br>
        <input required v-model="password" type="password" placeholder="Mot de passe" style="width:80%; font-size:20px; margin-bottom:80px;">
        <button type="submit" class="btn btn-dark">Inscription</button>
      </div>
    </form>
  </div>
</template>

<script>

import authService from "@/services/auth_service";

export default {
  name: "register",
  data() {
    return {
      username: '',
      email: '',
      password: '',
    }
  },
  methods: {
    inscription: function () {
      const _authService = new authService()
      _authService.register(this.username, this.email, this.password).then(
          (response) => {
            console.log(response);
          }
      )
    }
  }
}
</script>

<style scoped>

</style>
