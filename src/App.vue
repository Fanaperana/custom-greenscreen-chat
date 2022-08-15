<template>
  <div class="container h-full mx-auto">
    <div class="flex flex-col h-full p-6">
      <div class="grid content-end place-content-start" id="messageContainer">
        <MessageBubble v-for="(message, index) in messages" :message="message" :key="index" :keyid="index"/>
      </div>

      <div class="mx-auto mt-4 mb-10" style="width: 400px;">
        <div id="textCompose" class="text-bubble" contenteditable @keydown.enter.prevent="addToArray()"></div>
      </div>
      
    </div>

    
  </div>
</template>

<script>
import MessageBubble from '@/components/MessageBubble.vue'

export default {
  name: 'App',
  components: {
    MessageBubble
  },
  data: () => ({
    messages: [ ],
    mytext: ''
  }),
  methods: {
    addToArray () {
      const c = document.getElementById("textCompose");
      
      if (c.textContent) {
        this.messages.push(c.textContent);
        c.innerText='';
      }
      c.innerText='';
    }
  }
}
</script>

<style>
html,
body,
#app {
  width: 100%;
  height: 100%;
  padding: 0;
  margin: 0;
  background-color: #00B140;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  height: 100%;
  width: 100%;
}
#messageContainer{
  max-width: 400px;
  min-width: 400px;
  width: 400px;
  margin-left: auto;
  margin-right: auto;
  padding: 5px;
  height: 100%;
}
#textCompose{
  -moz-appearance: textfield-multiline;
  -webkit-appearance: textarea;
  border-radius: 15px;
  background-color: #E5E5EA;
  color: black;
  height:auto !important;
  resize: none;
  display: inline-block;
  max-width: 100%;
  text-align: justify;
}

#textCompose:focus{
  outline: none;
}

.text-bubble {
    max-width: 300px;
    word-wrap: break-word;
    margin-bottom: 12px;
    line-height: 24px;
    background-color: #e6e5ea;
    color: black;
    padding: 10px 20px;
    border-radius: 20px;
    position: relative;
    /* margin-left:auto; */
    margin-right:auto;
}

.text-bubble::before,
.text-bubble::after {
    content: "";
    width: 25px;
    height: 25px;
    position: absolute;
    bottom: 0;
}

.text-bubble::before {
    left: -7px;
    width: 20px;
    background-color: #E5E5EA;
    border-bottom-right-radius: 16px 14px;
}

.text-bubble::after {
    left: -26px;
    width: 26px;
    background-color: #00B140;
    border-bottom-right-radius: 10px;
}
</style>
