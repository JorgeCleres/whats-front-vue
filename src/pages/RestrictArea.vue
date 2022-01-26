<template>
  <q-page class="container full-height">
    <div>
      <ConversationArea />
    </div>

    <div v-if="1 == 1" class="column">
      <TopBar 
        :title="'Jorge Willian'"
      />
      <ChatArea />
      <MessageBar />
    </div>
    <Empty v-else />
  </q-page>
</template>

<script>
import Empty from '../components/Empty/Index.vue'
import ConversationArea from '../components/ConversationArea/Index.vue'
import TopBar from '../components/TopBar/Index.vue'
import ChatArea from '../components/ChatArea/Index.vue'
import MessageBar from '../components/MessageBar/Index.vue'
export default {
  name: 'RestrictArea',
  data() {
    return {
      
    }
  },
  components: {
    Empty,
    ConversationArea,
    TopBar,
    ChatArea,
    MessageBar
  }
}
</script>

<style lang="scss" scoped >
  .container {
    display: flex;
    overflow: hidden;
    min-width: 1200px;
  }
</style>