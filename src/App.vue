<template>
  <div id="app" class='app'>

    <div>
      <h1 class="app__title">Vue-Tac-Toe</h1>
    </div>

    <div>
      <GameBoard
      v-bind:boardSize='boardSize'  
      v-bind:activePlayer='activePlayer'
      v-on:change-active-player='changeActivePlayer($event)'
      />
    </div>

    <div class='app__currentplayer'>
      Current Player: {{activePlayer}}
    </div>

    <div class='app__winner'>
      {{winner? `${winner} wins!`: ''}}
    </div>

  </div>
</template>

<script>
import GameBoard from './components/GameBoard.vue';

export default {
  name: 'App',
  components: {
    GameBoard
  },
  data() {
    return {
      boardSize: [0,1,2,3,4,5,6,7,8],
      activePlayer: 'O',
      xScore: [0,0,0,0,0,0,0,0,0],
      oScore: [0,0,0,0,0,0,0,0,0],
      winner: ''
    }
  },
  methods: {
    changeActivePlayer(item) {
      if(this.activePlayer=='X'){
        this.xScore[item] = 1;
        this.checkForWinner(this.xScore, this.activePlayer, 'A');
        this.activePlayer ='O';
      } else if(this.activePlayer == 'O') {
        this.oScore[item] = 1;
        this.checkForWinner(this.oScore, this.activePlayer, 'B');
        this.activePlayer = 'X';
      }
    },
    checkForWinner(score, player, letter) {
      console.log(score, player, letter)
      
      //There should be 8 cases to win
      if(score[0]==1 && score[1]==1 && score[2]==1) {
        this.winner = player;
      } else if(score[3]==1 && score[4]==1 && score[5]==1) {
        this.winner = player;
      } else if(score[6]==1 && score[7]==1 && score[8]==1) {
        this.winner = player;
      } else if(score[0]==1 && score[3]==1 && score[6]==1){
        this.winner = player;
      } else if(score[1]==1 && score[4]==1 && score[7]==1) {
        this.winner = player;
      } else if(score[2]==1 && score[5]==1 && score[8]==1) {
        this.winner = player;
      } else if(score[0]==1 && score[4]==1 && score[8]==1) {
        this.winner = player;
      } else if(score[2]==1 && score[4]==1 && score[6]==1) {
        this.winner = player;
      }

    }
  }
}
</script>

<style>
  @import './styles/globals.css';
  @import './styles/App.css';
</style>
