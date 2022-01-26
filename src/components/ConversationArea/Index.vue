<template>
  <div class="conversation-area">
    <Header />
    <div class="card-area">
      <div 
        class="card row items-center justify-between q-px-md"
        v-for="item in 20"
        :key="item"
      >
        <q-avatar size="40px" class="q-mr-sm">
          <img src="https://i.pravatar.cc/40" alt="">
        </q-avatar>
        <div class="message column justfy-around full-height q-pt-sm">
          <div class="row justify-between">
            <div class="column">
              <span>Jorge WIllian</span>
              <span v-if="1 == 1">Nova mensagem recebida</span>
              <span v-else>Veja a nossa ultima conversa...</span>
            </div>
            <div class="column items-center justify-center">
              <span>16:31</span>
            </div>
          </div>
          <q-separator></q-separator>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'ConversarionArea',
  components: {
    Header
  }
})
</script>

<style lang="scss" scoped>
  .conversation-area{
    height: 100vh;
    width: 410px;
    background-color: #fff
  }
  .card-area {
    height: calc(100vh - 100px);
    overflow: auto
  }
  .card {
    background-color: #fff;
    height: 74px;
    &:hover {
      background-color: $grey-whats
    }
    cursor: pointer;
  }
  .q-avatar {
    flex-grow: 0.1
  }
  .message {
    flex-grow: 5;
    text-overflow: ellipsis;
    white-space: nowrap;
    overflow: hidden;
    width: 250px;

    span:first-child {
      font-size: 16px
    }
    span:last-child {
      font-size: 12px;
      color: $sub-title-grey;
    }
  }
</style>
