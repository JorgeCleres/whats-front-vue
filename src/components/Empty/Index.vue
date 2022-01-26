<template>
  <div class="empty">
    <div class="container full-width full-height column items-center justity-center">
      <q-img src="../../assets/whatsapp2.png" height="350px" width="350px"></q-img>
      <h4>Mantenha o celular conectado</h4>
      <span>
        O whatsapp web conecta ao seu telefone para sincronizar suas mensagen.
        Para diminuir o uso do seu plano de internet, conecte seu telefone a uma rede wi-fi
      </span>
    </div>
  </div>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'EmptyChat',
})
</script>

<style lang="scss" scoped>
  .empty {
    height: calc(100vh);
    min-width: 800px;
    width: calc(100vw - 410px);
    background-color: $empty-background
  }
  .container {
    h4{
      width: 350px;
      text-align: center;
      margin: 12px 0px;
      color: $font-empty;
    }
    span {
      width: 450px;
      text-align: center;
      color: $font-grey
    }
  }
</style>
