<template>
    <div>
      <h2>Component B</h2>
      <p>Received Message: {{ receivedMessage }}</p>
    </div>
  </template>
  
  <script>
  
  export default {
    data() {
      return {
        receivedMessage: ''
      };
    },
    created() {
      this.channel = new BroadcastChannel('myChannel');
      this.channel.onmessage = (event) => {
        this.receivedMessage = event.data;
        alert(event.data);
      };
    },
    beforeDestroy() {
      this.channel.close();
    }
  };
  </script>
  