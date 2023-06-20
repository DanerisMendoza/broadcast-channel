<template>
  <div>
    <h2>Component A</h2>
    <input v-model="message" type="text" />
    <button @click="sendMessage">Send Message</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: ''
    };
  },
  created() {
    this.channel = new BroadcastChannel('myChannel');
  },
  methods: {
    sendMessage() {
      this.channel.postMessage(this.message);
    }
  },
  beforeDestroy() {
    this.channel.close();
  }
};
</script>
