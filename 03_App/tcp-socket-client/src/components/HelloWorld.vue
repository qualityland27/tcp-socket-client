<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      Checkout our website
      <a href="https://volkert.net" target="_blank" rel="noopener">Volkert Webpage</a>.
    </p>
    <!-- <h3>Installed CLI Plugins</h3>
    <ul>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-babel" target="_blank"
          rel="noopener">babel</a></li>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-eslint" target="_blank"
          rel="noopener">eslint</a></li>
    </ul>
    <h3>Essential Links</h3>
    <ul>
      <li><a href="https://vuejs.org" target="_blank" rel="noopener">Core Docs</a></li>
      <li><a href="https://forum.vuejs.org" target="_blank" rel="noopener">Forum</a></li>
      <li><a href="https://chat.vuejs.org" target="_blank" rel="noopener">Community Chat</a></li>
      <li><a href="https://twitter.com/vuejs" target="_blank" rel="noopener">Twitter</a></li>
      <li><a href="https://news.vuejs.org" target="_blank" rel="noopener">News</a></li>
    </ul>
    <h3>Ecosystem</h3>
    <ul>
      <li><a href="https://router.vuejs.org" target="_blank" rel="noopener">vue-router</a></li>
      <li><a href="https://vuex.vuejs.org" target="_blank" rel="noopener">vuex</a></li>
      <li><a href="https://github.com/vuejs/vue-devtools#vue-devtools" target="_blank" rel="noopener">vue-devtools</a>
      </li>
      <li><a href="https://vue-loader.vuejs.org" target="_blank" rel="noopener">vue-loader</a></li>
      <li><a href="https://github.com/vuejs/awesome-vue" target="_blank" rel="noopener">awesome-vue</a></li>
    </ul> -->
  </div>
  <div>
    <h3>Connection</h3>
  </div>
  <div>
    <input type="text" v-model="ip" placeholder="IP Address" />
  </div>
  <div>
    <input type="text" v-model="port" placeholder="Port" />
  </div>
  <div>
    <button class="button button1" @click="connect">connect</button>
  </div>
  <div>
    <h3 class="w-20">Message:</h3>
  </div>  
  <div>
    <input type="text" v-model="message" />
  </div>
  <div>
    <button class="button button1" @click="sendMessage">send</button>  
  </div>
  <div>
    <button class="button button1" @click="read">read</button>
  </div>
  <div>
    <h3 class="w-20">{{ messageFromSocket }}</h3>
  </div>  
</template>

<script>
import net from 'net'

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      ip: '192.168.10.102',
      port: '1025',
      message: '1',
      returnMessage: 'none',
      messageFromSocket: 'none1'
    }
  },
  mounted() {
    const socket = new net.Socket()
    this.socket = socket
    socket.on('data', (data) => console.log(data.toString()))
    socket.on('data', (data) => this.messageFromSocket = data.toString())
  },
  methods: {
    connect() {
      console.log("in connect")
      console.log("ip: " + this.ip)
      console.log("port: " + this.port)
      this.socket.connect(this.port, this.ip)
      console.log(this.socket)
    },
    sendMessage() {
      console.log("in send message")
      this.socket.write(this.message)
      console.log(this.socket.returnMessage)

    },

    read() {
      console.log("in read message")
      // this.socket.read(this.returnMessage)
      // console.log(this.returnMessage)
      // this.socket.read(this.returnMessage)
      // console.log(this.returnMessage)
      // this.socket.read(this.returnMessage)
      // console.log(this.returnMessage)
      
      
      //this.socket.write("read")
      this.socket.read(this.returnMessage)
      console.log(this.returnMessage)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #3B498A;
}

input[type=text] {
  padding: 12px 20px;
  margin: 8px 0;
  border: none;
  border-bottom: 2px solid #2c3e50;
  /* border-radius: 12px; */
  background-color: transparent;
  color: #2c3e50;
}


.button1 {
  background-color: #2c3e50;
  padding: 12px 28px;
  border-radius: 12px;
  border: none;
  transition-duration: 0.4s;
  color: white;

}

.button1:hover {
  background-color: #6383a5;
}

</style>


