<script setup lang="ts">
import { ref } from "vue";
import type { Ref } from "vue";

interface Message {
  id: number;
  content: string;
  owner: string;
};

// References:
const messages: Ref<Message[]> = ref([]);
const input: Ref<string> = ref("");

function onSubmit() {
  let m: Message = { id: 1, owner: "user-message", content: input.value };
  input.value = "";
  messages.value.push(m);
}
</script>

<template>
  <div class="chat-container">
    <div class="message-container">
      <div class="user-message">
        This is a test message, user.
      </div>
      <div class="bot-message">
        This is a test message, user.
      </div>
      <div class="user-message">
        This is a test message, user.
      </div>
      <div v-for="m in messages" :class="m.owner" key="m.id">
        {{ m.content }}
      </div>
    </div>
    <div class="chat-form-container">
      <input type="text" v-model="input" v-on:keyup.enter="onSubmit" placeholder="Your input here...">
    </div>
  </div>
</template>

<style scoped>
/* General page settings: */
.chat-container {
  background-color: #242424;

  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  align-content: flex-start;

  font-size: 14px;
}

/* Message style */
.message-container {
  width: 90%;

  flex-grow: 1;
  overflow: auto;

  display: flex;
  flex-direction: column;
  
}

.message-container div {
  width: 70%;
  margin-bottom: 10px;
  padding: 8px 12px;
}

.message-container div.user-message {
  background-color: #454545;
  margin-left: auto;
  border-radius: 5px 0px 0px 5px;
}

.message-container div.bot-message {
  background-color: #14a484;
  margin-right: auto;
  border-radius: 0px 5px 5px 0px;
}

/* User form style: */
.chat-form-container {
  height: 10%;
  width: 100%;
  min-height: 100px;

  display: flex;
  justify-content: center;
  align-items: center;
}

.chat-form-container input[type=text] {
  width: 80%;
  padding: 8px 12px;
}
</style>
