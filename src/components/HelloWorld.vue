<template>
  <div class="main-block">

    <input class="input-character-search" v-model="characterSearch" type="text" placeholder="Search for any character or class.">
    <div class="characters">
      <div v-bind:key="character.id" v-for="character in charactersList">
        <div  data-toggle="modal" data-target="#single-character-modal" class="character-card" v-show="evaluateCharacterSearch(characterSearch, character.name)" v-on:click="getCurrentCharacterInfo(character)">
          <p>{{ character.name }}</p>
          <img class="character-image" v-bind:alt="character.alt" v-bind:src="'./assets/' + character.image">
        </div>
      </div>
    </div>


    <div class="container icon-container">
      <div class="row text-center align-items-center icon-row">
        <div class="col-12">
          <h5>to see more of my projects you can go to <a target="_blank" href="https://maurowernly.github.io/">maurowernly.github.io</a> or click on the following icons:</h5>
        </div>
          <div class="col-6">
              <a target="_blank" href="https://maurowernly.github.io/Pokedex/" class="d-block pkm-icon">
                  <img src="../../public/assets/images/stars.svg" alt="Sparkling stars" class="stars-pokedex">
                  <img src="../../public/assets/images/closed-pokedex.svg" alt="Closed Pokedex" class="closed-pokedex">
                  <img src="../../public/assets/images/open-pokedex.svg" alt="Closed Pokedex" class="open-pokedex">
              </a>
          </div>
          <div class="col-6">
              <a target="_blank" href="#" class="d-block pkm-icon">
                  <img src="../../public/assets/images/pokeball-closed.svg" alt="Closed Pokéball" class="pokeball-closed">
                  <img src="../../public/assets/images/pokeball-open.svg" alt="Closed Pokéball" class="pokeball-open">
              </a>
          </div>
      </div>
    </div>

    <div class="modal fade" id="single-character-modal" tabindex="-1" role="dialog">
      <div class="modal-dialog" role="document">
        <div class="modal-content ff7-bg">
          <div class="modal-header">
            <h5 class="modal-title current-character-title" id="exampleModalLabel">{{currentClickedCharacter.name}}</h5>
            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div class="modal-body">
            <div class="container">
              <div class="row">
                <div class="col-12 col-md-6">
                  <div class="image-pill">
                    <img class="current-haracter-image" v-bind:alt="currentClickedCharacter.alt" v-bind:src="'./assets/' + currentClickedCharacter.image">
                  </div>
                  <div class="under-img-info ff7 ff7-bg">
                    <p>Race: {{currentClickedCharacter.race}}</p>
                    <p>Class: {{currentClickedCharacter.class}}</p>
                    <p>Age: {{currentClickedCharacter.age}}</p>
                    <p>Origin: {{currentClickedCharacter.origin}}</p>
                  </div>
                </div>
                <div class="col-12 col-md-6">
                  <div class="right-pill-current-character ff7-bg">
                    <div class="quote-character">
                      {{currentClickedCharacter.quote}}
                    </div>
                    <div class="description-character">
                      {{currentClickedCharacter.description}}
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Characters from '../../public/assets/data/characters.json'

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return{
      charactersList: Characters,
      characterSearch: '',
      currentClickedCharacter: {}
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
    },
    getCurrentCharacterInfo: function(currentCharacter) {
      this.currentClickedCharacter = currentCharacter;
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
    background-color: #f6f6f6;
    border: 1px solid black;
    border-left: transparent;
    border-top: transparent;
    border-right: transparent;
    display: block;
    margin-left: auto;
    margin-right: auto;
    margin-bottom: 40px;
}
.input-character-search:hover,
.input-character-search:focus{
  box-shadow:
  0px 0px 0px 1.5px rgba(255, 255, 255,1),
  0px 0px 0px 3px rgba(0,0,0,1);
  background-color: black;
  color: white;
}

.characters {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
}

.character-card{
  display: inline-block;
  background-color: white;
  border: 1px solid black;
  margin: 20px 50px;
  min-width: 270px;
  max-width: 300px;
  box-shadow: 0px 0px 30px 10px rgba(0, 0, 0, 0.1);
  pointer-events: visible;
  cursor: pointer;
}

.character-image{
  max-height: 200px;
  width: auto;
}

.modal-dialog{
  max-width: 700px !important;
}

@media(max-width: 768px){
  .modal-dialog{
    max-width: 350px !important;
  }
  .modal-content{
    width: auto;
  }
}

.modal-title{
  margin-left: auto !important;
  color: white;
}

.modal-header button{
  color: white;
}

.current-character-title{
  text-align: center !important;
}

img.current-haracter-image{
  max-width: 140px;
  margin-top: 20px;
}

.quote-character{
  color: white;
  margin-bottom: 10px;
  margin-top: 40px;
  font-size: 19px;
}

.description-character{
  text-align: left;
  color: white;
}

.modal-header{
  text-align: center !important;
  color: white;
}

.under-img-info{
  margin-top: 30px;
}

.ff7-bg{
  border: solid 1px #424542;
  box-shadow: 1px 1px white,
              -1px -1px white,
              1px -1px white,
              -1px 1px white,
              0 -2px #9c9a9c,
              -2px 0 #7b757b,
              0 2px #424542;
  padding: 5px 15px;
  margin: 0px 25px;
  
  background: #04009d;
  background: linear-gradient(to bottom,  #04009d 0%,#06004d 100%);


  -webkit-border-radius: 7px;
  -moz-border-radius: 7px;
  border-radius: 7px;
}

div.ff7{
  margin-top: 40px;
  margin-left: -70px;
}

@media(max-width: 768px){
  div.ff7{
    margin-left: auto;
    margin-right: auto;
    display: block;
  }
}

div.ff7 *{
  color: white;
  text-shadow: 2px 2px #212421,
               1px 1px #212021;
  font-family: 'VT323', monospace;
  font-size: 17px;
  display: block;
  font-weight: normal;
  margin: 5px 0;
  text-align: left;
}

.right-pill-current-character{
  font-family: 'VT323', monospace;
  text-shadow: 2px 2px #212421, 1px 1px #212021;
  margin: 0;
  padding: 15px 10px;
  margin-top: 50px;
  max-width: 100%;
}

.image-pill{
  border: 2px solid #06004d;
  display: block;
  width: 200px;
  margin-left: auto;
  margin-right: auto;
  margin-top: 50px;
  background-color: white;
  border-radius: 7px;
}

.icon-row{
  margin-top: 60px;
  margin-bottom: 60px;
}

.icon-row h5{
  margin-bottom: 100px;
}

.icon-row a{
  color: black;
  text-decoration: underline;
}

.icon-row a:hover,
.icon-row a:focus{
  text-decoration: none;
  color: black;
}

a.pkm-icon{
    text-decoration: none;
    color: transparent;
    height: 100px;
    width: 100px;
    position: relative;
    margin: 0 auto;
}

@media (max-width: 768px){
    a.pkm-icon{
        transform: scale(.6);
    }
}

a .closed-pokedex{
    position: absolute;
    top: 50%;
    left: 50%;
    opacity: 1;
    max-width: 80px;
    transition: all .3s ease-in-out;
    transform: translate(-50%, -50%);
}

a:hover .closed-pokedex,
a:focus .closed-pokedex{
    opacity: 0;
    transform: translate(-100%, -50%);
}

a .open-pokedex{
    position: absolute;
    top: 50%;
    left: 50%;
    max-width: 180px;
    opacity: 0;
    transition: all .15s ease-in-out;
    transform: translate(0%, -50%);
}

a:hover .open-pokedex,
a:focus .open-pokedex{
    opacity: 1;
    max-width: 135px;
    transform: translate(-50%, -50%);
}

a .stars-pokedex{
    position: absolute;
    top: 0;
    left: 50%;
    transform: scale(.8) translate(-50%, -125%);
    transform-origin: 50% 100%;
    transition: all .2s ease-in-out;
    opacity: 0;
    max-width: 100px;
}

a:hover .stars-pokedex,
a:focus .stars-pokedex{
    transform: scale(1) translate(-50%, -125%);
    opacity: 1;
}

a .pokeball-closed{
    position: absolute;
    bottom: 0;
    left: 50%;
    max-width: 100px;
    transform: translateX(-50%) rotate(0deg);
    transition: all .2s ease-in-out;
}

@keyframes spin1 {
    0% { transform: translateX(-50%) rotate(0deg);}
    80% { transform: translateX(-50%) rotate(180deg);}
    100% { 
        opacity: 0;
    }
}

a:hover img.pokeball-closed,
a:focus img.pokeball-closed{
    animation: spin1 .7s ease-in-out forwards;
}


a .pokeball-open{
    position: absolute;
    left: 50%;
    bottom: 0;
    opacity: 0;
    max-width: 160px;
    transform: translateX(-50%);
}

@keyframes fade-in-pkm {
    0% { opacity: 0;}
    100% { opacity: 1;}
}

a:hover .pokeball-open,
a:focus .pokeball-open{
    animation-delay: .7s;
    animation: fade-in-pkm .8s ease-in-out forwards;
}
</style>
