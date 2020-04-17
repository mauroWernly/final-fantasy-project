<template>
  <div class="main-block">

    <input class="input-character-search" v-model="characterSearch" type="text" placeholder="Search for any character or class.">
    <div v-bind:key="character.id" v-for="character in charactersList">
      <div v-show="evaluateCharacterSearch(characterSearch, character.name)">
        <p>{{ character.name }}</p>
        <img class="character-image" v-bind:alt="character.alt" v-bind:src="'./assets/' + character.image">
      </div>
    </div>
    <li><a href="https://github.com/vuejs/awesome-vue" target="_blank" rel="noopener">awesome-vue</a></li>
  </div>
</template>

<script>
import Characters from '../../public/assets/data/characters.json'

export default {
  name: 'HelloWorld',
  props: {
    msg: String,
    characterSearch: String
  },
  data(){
    return{
      charactersList: Characters
    }
  },
  methods:{
    evaluateCharacterSearch: function (characterSearch, characterName) {
      if(characterName.toLowerCase().includes(characterSearch.toLowerCase())){
        return true;
      }
      else{
        return false;
      }
    }
  }
};

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import url('https://fonts.googleapis.com/css2?family=VT323&display=swap');

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
  color: #42b983;
}

.main-block{
  font-family: 'VT323', monospace;
}

.input-character-search{
    font-family: 'VT323', monospace;
    font-size: 24px;
    min-width: 350px;
    line-height: 36px;
    text-align: center;
    margin-top: 60px;
    border: 1px solid black;
    border-left: transparent;
    border-top: transparent;
    border-right: transparent;
}
.input-character-search:hover,
.input-character-search:focus{
  box-shadow:
  0px 0px 0px 1.5px rgba(255, 255, 255,1),
  0px 0px 0px 3px rgba(0,0,0,1);
  background-color: black;
  color: white;
}

.character-image{
  max-width: 200px;
}

</style>
