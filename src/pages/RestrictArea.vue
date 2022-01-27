<template>
  <q-page class="container full-height">
    <div>
      <ConversationArea
        :users = "users"
        @selectedItem="setCurrentItem"
      />
    </div>

    <div v-if="selectedItem" class="column">
      <TopBar 
        :title="nameConversation"
      />
      <ChatArea 
        :currentUser="selectedItem"
        :newMessages="newMessages"
      />
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
import api from 'src/services/api'
import { socket } from "src/services/socket"
import { notify } from "src/utils"

export default {
  name: 'RestrictArea',
  data() {
    return {
      users: [],
      newMessages: "",
      selectedItem: null,
      nameConversation: ""
    }
  },
  components: {
    Empty,
    ConversationArea,
    TopBar,
    ChatArea,
    MessageBar
  },
  created() {
    const receiver = localStorage.getItem('receiver');
    socket.on(receiver, message => {
      const arr = [];
      this.users.forEach(item => {
        console.log('teste')
        if( item.id ===  message.user_id) {
          item.newMessages = true
        }
        arr.push(item)
      });
      this.newMessages  = message.id;
      this.users = arr;
    })
  },
  async mounted() {
    await api.get("/users")
    .then( response => {
      this.users = response.data
    }).catch( () => {
      notify('negative', 'Falha ao listar usuários')
    })
  },
  methods: {
    async setCurrentItem({ id, email }) {
      this.selectedItem = id;

      await api
        .get(`user/${email}`)
        .then( response => {
          this.nameConversation = response.data.name
        })
        .catch( () => {
          this.nameConversation = "Novo usuário"
        })
    }
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