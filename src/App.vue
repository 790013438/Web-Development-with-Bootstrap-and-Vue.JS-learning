<template>
  <div id="app">
    <div v-for="message in messages"
      :key="message.id">
      <h4>{{ message.title }}</h4>
      <p>{{ message.text }}</p>
      <p>{{ message.timestamp }}</p>
    </div>
  </div>
</template>

<script>
import Firebase from 'firebase'

let config = {
  apiKey: 'AIzaSyAM_Q7pMQnbCXbvxJE19s4Gw312hZuIEoM',
  authDomain: 'presentfloyd.firebaseapp.com',
  databaseURL: 'https://presentfloyd.firebaseio.com',
  projectId: 'presentfloyd',
  storageBucket: 'presentfloyd.appspot.com',
  messagingSenderId: '801323269585'
}

let app = Firebase.initializeApp(config)
let db = app.database()
let messagesRef = db.ref('messages')
export default {
  firebase: {
    messages: messagesRef
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
