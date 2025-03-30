<script setup lang="ts">
import { ref, computed, onMounted } from 'vue'

defineProps<{ msg: string }>()

const count = ref(0)
const messages = ref<string[]>([]);

onMounted(async () => {
  const response = await fetch('./src/assets/messages.json');
  const data = await response.json();
  messages.value = data;
});

const currentMessage = computed(() => messages.value[count.value]);

const nextMessage = () => {
  count.value = (count.value + 1) % messages.value.length;
};
</script>

<template>
  <div class="dialog">
    <p class="text">{{ currentMessage }}</p>
    <br />
    <button class="button" @click="nextMessage"> ,סיימתי לקרוא<br />אפשר להמשיך
    </button>
    <!-- <input
      type="text"
      class="newMessage"
    />
    <button class="addNewMessage" @click="addNewMessage">
      <span class="addNewMessageText">הוספת הודעה חדשה</span>
    </button> -->
  </div>
</template>

<style scoped>

.dialog {
  height: 85vh;
  width: 90vw;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
}

.text {
  color: #FAB12F;
  /* border-color: #170f02; */
  font-size: 20px;
  text-align: center;
  margin-bottom: 20px;
}

.button {
  background: none;
  border: 2px solid #FBD288;
  color: #FBD288;
  font-size: 16px;
  padding: 10px 20px;
  cursor: pointer;
  transition: all 0.3s ease-in-out;
  text-align: center;
  display: block;
  margin: 0 auto;
  border-radius: 5px;
}

.button:hover {
  background: #FBD288;
  color: #FF9C73;
  border-color: #FF9C73;
}

.button:active {
  transform: scale(0.95);
}

.button:focus {
  outline: none;
}


</style>
