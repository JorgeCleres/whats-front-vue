<template>
    <div class="message-bar row items-center">
        <div class="q-mx-md">
        <q-btn
            round 
            dense 
            unelevated 
            icon="lar la-grin-alt"
            size="15px"
            text-color="grey"
            class="q-mr-sm"
        ></q-btn>

        <q-btn
            round 
            dense 
            unelevated 
            icon="las la-paperclip"
            size="15px"
            text-color="grey"
            class="q-mr-sm"
        ></q-btn>
        </div>

        <q-input
            rounded
            outlined
            v-model="text"
            label="Digite uma mensagem"
            bg-color="white"
            class="input-message"
        ></q-input>

        <q-btn
            round 
            dense 
            unelevated 
            :icon="text !== '' ? 'send' : 'fas fa-microphone'"
            size="13px"
            text-color="grey"
            class="q-mr-sm"
        ></q-btn>
    </div>
</template>

<script>
export default {
  name: 'MessageBar',
  data() {
    return {
        text: ""
    }
  }
}
</script>

<style lang="scss" scoped>
    .message-bar {
        height: 62;
        background-color: $grey-whats;

        .input-message {
            width: 86%;
        }
    }
</style>