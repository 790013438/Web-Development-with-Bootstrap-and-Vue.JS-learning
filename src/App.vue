<template>
  <div id="app" class="jumbotron">
    <div class="container">
      <h1>Hello! Nice to meet you!</h1>
      <hr />
      <form @submit="addMessage">
        <div class="form-group">
          <input class="form-control" v-model="newMessage.title"  maxlength="40" autofocus placeholder="Please introduce yourself :)" />
        </div>
        <div class="form-group">
          <textarea class="form-control" v-model="newMessage.text" placeholder="Leave your messsage!" row="3"></textarea>
        </div>
        <button class="btn btn-primary" type="submit">Send</button>
      </form>
      <hr />
      <div class="card-columns">
        <div class="card" v-for="message in reverse(messages)"
             :key="message.id">
          <div class="card-block">
            <h5 class="card-title">{{ message.title }}</h5>
            <p class="card-text">{{ message.text }}</p>
            <p class="card-text"><small class="text-muted">Added on {{ dateToString(message.timestamp) }}</small></p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Firebase from 'firebase'
import { dateToString, reverse } from './utils/utils'

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
  data () {
    return {
      newMessage: {
        title: '',
        text: '',
        timestamp: null
      }
    }
  },
  methods: {
    addMessage (e) {
      e.preventDefault()
      if (this.newMessage.title === '') {
        return
      }
      this.newMessage.timestamp = Date.now()
      messagesRef.push(this.newMessage)
      this.newMessage.text = ''
      this.newMessage.title = ''
      this.newMesage.timestamp = null
    },
    dateToString,
    reverse
  },
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
