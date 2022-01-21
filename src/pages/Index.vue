<template>
  <q-page class="flex flex-center">
    <div>
      <h5>Acesse o chat</h5>
      <q-input rounded outlined v-model="email" lavel="informe seu email" bg-color="white" class="q-mb-md"></q-input>
      <q-btn :riple="false" color="secondary" label="Acessar Chat"></q-btn>
    </div>
    <q-separator vertical></q-separator>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'PageIndex',
  data() {
    return {
      email: ""
    }
  }
})
</script>
