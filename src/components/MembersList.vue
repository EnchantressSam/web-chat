<template>
    <div>
      <h3>Members</h3>
      <ul class="members-list">
        <li v-for="member in members" :key="member.name">
          <span>{{ member.name }}</span>
          <span :class="member.online ? 'online' : 'offline'">{{ member.online ? 'online' : 'offline' }}</span>
        </li>
      </ul>
    </div>
  </template>

<script>
export default {
  props: {
    members: Array
  }
}
</script>

  <style scoped>
  .members-list {
    list-style-type: none;
    padding: 0;
  }

  .members-list li {
    display: flex;
    justify-content: space-between;
    padding: 10px 0;
  }

  .online {
    color: green;
  }

  .offline {
    color: red;
  }
  </style>
