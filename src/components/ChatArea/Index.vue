<template>
    <div class="chat-area">
        <div class="image full-width full-height">
            <Message 
                v-for="item in 10"
                :key="item"
                :text="'nova mensagem'"
                :hour="'18:48'"
                :my="true"

            ></Message>
        </div>
    </div>
</template>

<script>
import Message from 'src/components/Message/Index'
export default {
  name: 'MessageBar',
  components: {
      Message
  },
  data() {
    return {}
  }
}
</script>

<style lang="scss" scoped>
    .chat-area {
        height: calc(100vh - 59px - 62px);
        min-width: 800px;
        width: calc(100vw - 410px);
        background-color: $grey-background;
    }
    .image {
        background-image: url('../../assets/8c98994518b575bfd8c949e91d20548b.jpg');
        overflow: auto;
        display: flex;
        flex-direction: column-reverse;
    }
</style>