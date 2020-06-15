<template>
    <v-container class="container-cadastro">
        <v-btn @click="$emit('login', true)" class="ma-1 btn" tile outlined color="indigo lighten-2">
            <v-icon left>mdi-close</v-icon> Fechar
        </v-btn>
        <v-form ref="form">
            <h2 class="text-uppercase font-weight-thin">Cadastre uma conta</h2>
            <v-text-field v-model="user.name" label="Nome"></v-text-field>
            <v-text-field v-model="user.email" label="Email"></v-text-field>
            <v-row>
                <v-col cols="12" sm="12" md="6" lg="6">
                    <v-text-field v-model="user.password" :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'" :type="show1 ? 'text' : 'password'" 
                    label="Senha" hint="Pelo menos 8 caracteres" counter @click:append="show1 = !show1"></v-text-field>
                </v-col>
                <v-col cols="12" sm="12" md="6" lg="6">
                    <v-text-field :append-icon="show2 ? 'mdi-eye' : 'mdi-eye-off'" :type="show2 ? 'text' : 'password'" 
                    label="Senha" hint="Pelo menos 8 caracteres" counter @click:append="show2 = !show2"></v-text-field>
                </v-col>
            </v-row>
            <v-row>
                <v-col cols="12" sm="12" md="6" lg="6">
                    <v-text-field v-model="user.date_birth" label="Data de nascimento" type="date"></v-text-field>
                </v-col>
                <v-col cols="12" sm="12" md="6" lg="6">
                    <v-select v-model="user.genre" :items="genre" label="Gênero" required></v-select>
                </v-col>
            </v-row>
            <v-btn outlined color="light-blue lighten-2" @click="clear">Limpar formulário</v-btn>
            <v-btn color="light-green" class="float-right white--text" @click="submit">submit</v-btn>
        </v-form>
    </v-container>
</template>

<script>
export default {
    data() {
        return {
            user: {
                name: '',
                email: '',
                password: '',
                genre: '',
                date_birth: ''
            },
            show1: false,
            show2: false,
            genre: [ 'Feminino', 'Masculino', 'Outro' ],
        }
    },
    methods: {
        submit(){
            alert('Foi')
        },
        clear(){
            this.$refs.form.reset()
        }
    }
}
</script>

<style>
.container-cadastro{
    padding: 5% 10%;
    height: 100vh;
    display: flex;
    align-items: center;
}
form{
    width: 100%;
}
.btn{
    position: absolute;
    top: 10px;
}
</style>