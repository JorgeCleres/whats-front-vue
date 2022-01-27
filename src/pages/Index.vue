<template>
  <q-page class="row items-center justify-center">
    <div class="container image q-pa-xl">
      <h5>Acesse o chat</h5>
      <q-input 
        rounded
        outlined
        v-model="email"
        label="informe seu email"
        bg-color="white"
        class="q-mb-md">
      </q-input>

      <q-btn
        :riple="false"
        color="secondary"
        label="Acessar Chat"
        @click="signIn()"
      ></q-btn>
    </div>
    <q-separator vertical></q-separator>
    <div class="container q-pa-xl">
      <h5>Cadastre-se</h5>
      <q-input 
        rounded
        outlined
        v-model="name"
        label="informe seu nome"
        bg-color="white"
        class="q-mb-md">
      </q-input>

      <q-input 
        rounded
        outlined
        v-model="emailSingUp"
        label="informe seu email"
        bg-color="white"
        class="q-mb-md">
      </q-input>

      <q-btn
        :riple="false"
        color="secondary"
        label="Cadastrar"
        no-caps
        @click="signUp()"
      ></q-btn>
    </div>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue';
import { notify } from 'src/utils'
import api from 'src/services/api'
import crypto from 'crypto'

export default defineComponent({
  name: 'PageIndex',
  data() {
    return {
      email: "",
      name: "",
      emailSingUp: "",
    }
  },
  watch: {
    email() {
      if(this.email !== "") {
        this.name = "";
        this.emailSingUp = ""
      }
    },
    name() {
      if(this.name !== "") this.email = ""
    },
    emailSingUp() {
      if(this.emailSingUp !== "") this.email = ""
    }
  },
  methods:{
    async signIn() {
      if(this.email === "") {
        this.fail("Preencha o campo de e-mail")
      } else {
          await api.get(`/user/${this.email}`)
            .then( response => {
            this.sucess('Login efetuado com sucesso', response.data.id)
            console.log(response.data.id)
          }).catch( error => {
            notify('negative', error.response.data.message)
          })
        }
    },
    async signUp() {
      if(this.emailSingUp === "" || this.name === "") {
        this.fail("Preencha o campo de e-mail e/ou nome")
      } else {
          await api.post("user", {name: this.name, email: this.emailSingUp})
            .then( response => {
            this.sucess('Cadastro efetuado com sucesso', response.data.id)
            consolo.log(response)
          }).catch( error => {
            notify('negative', error.response.data.message)
          })
        }
    },
    sucess(message, id) {
        notify('positive', message)
        this.$router.push({ path: "chat"});
        const receiver = crypto.createHash("md5").update(`${id}`).digest("hex")
        localStorage.setItem("receiver", receiver)
        localStorage.setItem("myId", id)
        console.log(id)
    },
    fail(message) {
      notify('negative', message)
    }
  }
})
</script>

<style lang="scss" scoped>
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 48%;
      h5 {
        color: #444444;
      }
      .q-btn,
      .q-input {
        width: 300px;
      }
  }
  .image {
    background-image: url('../assets/8c98994518b575bfd8c949e91d20548b.jpg');
    height: 60vw;
    width: 48%;
    background-size: cover;
  }
</style>
