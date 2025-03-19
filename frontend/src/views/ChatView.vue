<script setup lang="ts">
import Chat from "../components/Chat.vue";
import ConversationSelect from "../components/ConversationSelect.vue";
</script>

<template>
  <main class="chat-view-main">
    <div class="chat-view-convo-list">
      <ConversationSelect />
    </div>
    <div class="chat-view-chat">
        <Chat />
    </div>
  </main>
</template>

<style scoped>
.chat-view-main {
  background-color: #242424;
  width: 100%;
  height: 100%;
  
  display: flex;
  justify-content: center;
}

.chat-view-convo-list {
  width: 20%;
  height: 100%;
  border: 1px solid black;
  box-shadow: 2px 0px 4px black;
}

.chat-view-chat {
  width: 80%;
  height: 100%;
}
</style>
