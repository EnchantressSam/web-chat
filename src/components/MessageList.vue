<template>
    <div class="message-list">
      <div v-for="message in messages" :key="message.id" class="message">
        <div class="message-content">
          <!-- Имя автора сообщения жирным шрифтом слева сверху -->
          <p class="message-author">{{ message.user }}</p>
          <!-- Само сообщение будет отображаться под именем -->
          <p class="message-text">{{ message.text }}</p>
          <!-- Дата и время справа внизу -->
          <span class="message-timestamp">{{ formatTimestamp(message.timestamp) }}</span>
        </div>
      </div>
    </div>
  </template>

<script>
export default {
  name: 'MessageList',
  props: {
    messages: {
      type: Array,
      required: true
    }
  },
  methods: {
    // Форматирование переданного времени (timestamp)
    formatTimestamp (timestamp) {
      const date = new Date()
      const hours = date.getHours().toString().padStart(2, '0')
      const minutes = date.getMinutes().toString().padStart(2, '0')
      const seconds = date.getSeconds().toString().padStart(2, '0')
      const formattedDate = date.toLocaleDateString()

      return `${hours}:${minutes}:${seconds} ${formattedDate}`
    }
  }
}
</script>

  <style scoped>
  .message-list {
    flex: 1;
    padding: 20px;
    overflow-y: auto; /* Прокрутка по вертикали */
    background-color: #f7f7f7; /* Фон всего списка сообщений */
  }

  .message {
    background-color: #e0f7fa; /* Светлый цвет фона сообщения (похожий на верхнее меню) */
    padding: 10px;
    margin-bottom: 10px;
    border-radius: 5px;
    display: flex;
    flex-direction: column;
  }

  .message-content {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
  }

  /* Имя автора сообщения */
  .message-author {
    font-weight: bold;
    color: #00796b; /* Тот же цвет, что и у верхнего меню */
    margin-bottom: 5px;
  }

  /* Текст сообщения */
  .message-text {
    margin: 0;
    padding-bottom: 10px; /* Отступ снизу */
    text-align: left;
    flex: 1;
  }

  /* Дата и время сообщения */
  .message-timestamp {
    font-size: 0.85em;
    color: #9e9e9e;
    align-self: flex-end; /* Выровняем по правой стороне */
    margin-top: auto;
  }
  </style>
