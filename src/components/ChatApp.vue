<template>
    <div class="chat-container">
      <!-- Header -->
      <header class="chat-header">
        <div class="chat-title">Chat</div>
        <div class="user-info">
          <span>{{ user.name }}</span> | <a href="#">Logout</a>
        </div>
      </header>

      <div class="chat-body">
        <!-- Left: Channels list -->
        <aside class="channels">
          <ChannelsList :channels="channels" @selectChannel="selectChannel" />
        </aside>

        <!-- Center: Messages area -->
        <section class="messages">
          <MessageList :messages="currentMessages" />
          <MessageInput @sendMessage="addMessage" />
        </section>

        <!-- Right: Members list -->
        <aside class="members">
          <MembersList :members="currentChannelMembers" />
        </aside>
      </div>
    </div>
  </template>

<script>
import ChannelsList from './ChannelsList.vue'
import MessageList from './MessageList.vue'
import MembersList from './MembersList.vue'
import MessageInput from './MessageInput.vue'

export default {
  components: {
    ChannelsList,
    MessageList,
    MembersList,
    MessageInput
  },
  data () {
    return {
      user: { name: 'Sorceress' },
      channels: ['Lut Golein', 'Kurast', 'Dark Wood'],
      messages: {
        General: [{ user: 'Sorceress', text: 'Feel free to talk about anything here.', time: new Date() }],
        Weapons: [],
        Combat: []
      },
      members: {
        General: [{ name: 'Sorceress', online: true }, { name: 'Barbarian', online: false }, { name: 'Paladin', online: false }],
        Weapons: [{ name: 'Sorceress', online: true }, { name: 'Barbarian', online: false }, { name: 'Paladin', online: false }],
        Combat: [{ name: 'Sorceress', online: true }, { name: 'Barbarian', online: false }, { name: 'Paladin', online: false }]
      },
      currentChannel: 'General'
    }
  },
  computed: {
    currentMessages () {
      return this.messages[this.currentChannel]
    },
    currentChannelMembers () {
      return this.members[this.currentChannel]
    }
  },
  methods: {
    selectChannel (channel) {
      this.currentChannel = channel
    },
    addMessage (messageText) {
      const newMessage = {
        user: this.user.name,
        text: messageText,
        time: new Date()
      }
      this.messages[this.currentChannel].push(newMessage)
    }
  }
}
</script>

  <style scoped>
  /* Основные стили */
  .chat-container {
    display: flex;
    flex-direction: column;
    height: 100vh;
  }

  .chat-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: #009dc4;
    padding: 10px 20px;
    color: white;
  }

  .chat-body {
    display: flex;
    flex: 1;
  }

  .channels, .members {
    width: 20%;
    border-right: 1px solid #ddd;
    padding: 20px;
  }

  .messages {
    flex: 1;
    padding: 20px;
    display: flex;
    flex-direction: column;
  }

  .message-input {
    margin-top: auto;
  }

  </style>
