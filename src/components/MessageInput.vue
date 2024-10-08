<template>
    <div class="message-input">
      <input v-model="message" @keyup.enter="sendMessage" placeholder="Enter Message" />
      <button @click="sendMessage">Send</button>
    </div>
  </template>

<script>
export default {
  data () {
    return {
      message: ''
    }
  },
  methods: {
    sendMessage () {
      if (this.message.trim()) {
        this.$emit('sendMessage', this.message)
        this.message = ''
      }
    }
  }
}
</script>

  <style scoped>
  .message-input {
    display: flex;
    margin-top: auto;
  }

  .message-input input {
    flex: 1;
    padding: 10px;
  }

  .message-input button {
    background-color: #009dc4;
    color: white;
    padding: 10px;
    border: none;
    cursor: pointer;
  }
  </style>
