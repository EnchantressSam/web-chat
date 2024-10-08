<template>
    <div>
      <h3>Channels</h3>
      <ul class="channels-list">
        <li v-for="channel in channels" :key="channel" @click="selectChannel(channel)" :class="{ active: isActive(channel) }">
          # {{ channel }}
        </li>
      </ul>
    </div>
  </template>

<script>
export default {
  props: {
    channels: Array
  },
  methods: {
    selectChannel (channel) {
      this.$emit('selectChannel', channel)
    },
    isActive (channel) {
      return channel === this.$parent.currentChannel
    }
  }
}
</script>

  <style scoped>
  .channels-list {
    list-style-type: none;
    padding: 0;
  }

  .channels-list li {
    padding: 10px;
    cursor: pointer;
  }

  .channels-list li.active {
    background-color: #009dc4;
    color: white;
  }
  </style>
