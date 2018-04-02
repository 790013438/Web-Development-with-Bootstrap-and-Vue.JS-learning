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
        <MessageCard class="card card-outline-success"
          :title="'Hello!'"
          :text="'This is our fixed card!'"
          :footer="'Add on ' + dateToString(Date.now())"></MessageCard>
        <MessageCard v-for="message in messages"
          :title="message.title"
          :text="message.text"
          :footer="'Added on ' + dateToString(message.timestamp)"
          :key="message.id"></MessageCard>
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
  },
  components: {
    MessageCard
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
