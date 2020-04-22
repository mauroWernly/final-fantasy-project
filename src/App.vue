  <template>
  <div id="app">
    <img width="500" height="168" alt="Final fantasy logo" class="ff-logo" src="../public/assets/logo.png">
    <HelloWorld msg="Welcome my Final Fantasy app made with Vue.js"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 30px;
}

body {
  background-color: #f6f6f6 !important;
}

img.ff-logo{
  max-width: 500px;
}

@media(max-width: 768px){
  img.ff-logo{
    max-height: 100px;
    width: auto;
  }
}
</style>
