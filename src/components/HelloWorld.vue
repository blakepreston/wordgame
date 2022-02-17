<template>

<div class="container">
  <div>
      <h1>Word Game</h1>
      <div class="cluesContainer">
        <p class="pointsClue">Your guess should equal to {{guessPoints}}.</p>
        <p>You have {{numGuesses}} guesses left.</p>
      </div>
      
    </div>

    <h2>Points: {{points}}</h2>
    <h2>Word: {{word}}</h2>

    <div class="mainContainer">
      <div class="letterContainer is-multiline">
        <div class="column" v-for="(item, index) in list" v-bind:key="item.letter" @click="getIndex(index)">
          <div>
            <h3>{{item.letter}}</h3>
            <h4>{{item.value}}</h4>
          </div>
        </div>
        <div class="enterButton" @click="checkWord()"><h2>Enter</h2></div>
      </div>
    </div>

</div>
  
</template>

<script>
export default {
  data(){
    return{
      list: [
        {letter: 'Q', value: 1},
        {letter: 'W', value: 2},
        {letter: 'E', value: 12},
        {letter: 'R', value: 6},
        {letter: 'T', value: 6},
        {letter: 'Y', value: 2},
        {letter: 'U', value: 4},
        {letter: 'I', value: 9},
        {letter: 'O', value: 8},
        {letter: 'P', value: 2},
        {letter: 'A', value: 9},
        {letter: 'S', value: 4},
        {letter: 'D', value: 4},
        {letter: 'F', value: 2},
        {letter: 'G', value: 3},
        {letter: 'H', value: 2},
        {letter: 'J', value: 1},
        {letter: 'K', value: 1},
        {letter: 'L', value: 4},
        {letter: 'Z', value: 1},
        {letter: 'X', value: 1},
        {letter: 'C', value: 2},
        {letter: 'V', value: 2},
        {letter: 'B', value: 2},
        {letter: 'N', value: 6},
        {letter: 'M', value: 2}
      ],
      points: 0,
      wordArray: [],
      letterIndex: 0,
      word: '',
      guessWord: "FIESTY",
      guessPoints: 33,
      numGuesses: 5
    }
  },
  methods:{
    getIndex(index){
      this.letterIndex = index;
      let letterData = this.list[this.letterIndex];
      this.wordArray.push(letterData);

      this.word += letterData.letter.toString();
      if(this.word.length > 6){
        alert("The word is too big!")
       let newString = this.word.slice(0,6)
       this.word = newString;
      }

      if(this.word.length < 6){
        this.points = 0;
        for(let i = 0; i < this.wordArray.length; i++){
          this.points += this.wordArray[i].value;
        }
      }
    },
    checkWord(){
      if(this.guessWord === this.word){
        alert("You did it!")
        this.endGame();
      }else{
        alert("Your guess is incorrect!")
        this.numGuesses--;
        this.endGame();
      }
    },
    endGame(){
      this.word = "";
      this.points = 0;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.mainContainer{
  width: 100%;
  margin-top: 5vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

h1,h2,p{
  color: #2DE2E6;
}

p{
  margin: 0;
}

h3 {
  cursor: pointer;
  margin: 0;
  font-size: 12px;
  color: #2DE2E6;
}

h4{
  cursor: pointer;
  margin: 0;
  font-size: 10px;
  color: #2DE2E6;
}

.enterButton{
  width: 20vw;
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #261447;
  height: 10vh;
  border-radius: 15px;
  margin: 5px;
}

.column{
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #261447;
  height: 10vh;
  margin: 5px;
  flex: 1;
  flex-basis: 15%;
  border-radius: 15px;
}

.letterContainer{
  width: 90%;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}

</style>
