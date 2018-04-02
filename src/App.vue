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
        <message-card class="card card-outline-success"
          :message="firstMessage"></message-card>
        <message-card v-for="message in messages"
          :message="message"
          :key="message.id"></message-card>
      </div>
    </div>
  </div>
</template>

<script>
import Firebase from 'firebase'
import { dateToString, reverse } from './utils/utils'
import MessageCard from './components/MessageCard.vue'

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
let FIRST_MESSAGE_TEXT = 'I created this page using Vue.js, Bootstrap and Firebase. ' +
    'The tutorial of this web page is described in the first part of the "Web Development with Bootstrap and Vue.js" book. ' +
    'If you are reading it at the moment, thanks a lot! ' +
    'I am also the author of "Learning Vue.js 2" book. I like Vue.js very much. ' +
    'I also love studying and teaching, reading and writing, skiing and diving. ' +
    'It\'s a great pleasure meeting you!'
export default {
  data () {
    return {
      firstMessage: {
        isFirst: true,
        title: 'Hello I am Olga',
        text: FIRST_MESSAGE_TEXT,
        timestamp: Date.now()
      },
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
  },
  components: {
    MessageCard
  }
}
</script>
