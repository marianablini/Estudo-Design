<template>
  <v-container class="container-login">
    <v-card class="mx-auto pa-5" cols="12" sm="12" md="6" lg="6">
      <v-card-text>
        <v-text-field v-model="email" label="Email" required></v-text-field>
        <v-text-field v-model="password" label="Senha" required></v-text-field>
      </v-card-text>
      <v-row>
        <v-col cols="12" class="pa-0 text-center">
          <v-btn class="white--text" color="light-green"> Entrar </v-btn>
        </v-col>
        <v-col class="text-center" cols="12">
           Não tem uma conta?<v-btn @click="$emit('cadastro', true)" text color="blue">Cadastre aqui!</v-btn>
        </v-col>
      </v-row>
    </v-card>
  </v-container>
</template>

<script>
  export default {
    data() {
      return {
        email: '',
        password: ''
      }
    },
  }
</script>

<style scoped>
.container-login {
  height: 100vh;
  display: flex;
  align-items: center;
}
</style>