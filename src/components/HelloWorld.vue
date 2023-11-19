<script setup>
import { ref } from 'vue'

let player = ref('X')

let Xplayer = []
let Oplayer = []

let gameState = {
  sq1: ref('G'),sq2: ref('G'),sq3: ref('G'),
  sq4: ref('G'),sq5: ref('G'),sq6: ref('G'),
  sq7: ref('G'),sq8: ref('G'),sq9: ref('G')
}

let gameComplete = false;

function sqClick(sqnum) {
  console.log('sqClick', sqnum)
  
  if (player.value == 'X') {
    Xplayer.push(sqnum)

    switch(sqnum){
      case 1:
        gameState.sq1.value = 'X'
        break
      case 2:
        gameState.sq2.value = 'X'
        break
      case 3:
        gameState.sq3.value = 'X'
        break
      case 4:
        gameState.sq4.value = 'X'
        break
      case 5:
        gameState.sq5.value = 'X'
        break
      case 6:
        gameState.sq6.value = 'X'
        break
      case 7:
        gameState.sq7.value = 'X'
        break
      case 8:
        gameState.sq8.value = 'X'
        break
      case 9:
        gameState.sq9.value = 'X'
        break
    }
  } 

  if (player.value == 'O') {

    Oplayer.push(sqnum)
    switch(sqnum){
      case 1:
        gameState.sq1.value = 'O'
        break
      case 2:
        gameState.sq2.value = 'O'
        break
      case 3:
        gameState.sq3.value = 'O'
        break
      case 4:
        gameState.sq4.value = 'O'
        break
      case 5:
        gameState.sq5.value = 'O'
        break
      case 6:
        gameState.sq6.value = 'O'
        break
      case 7:
        gameState.sq7.value = 'O'
        break
      case 8:
        gameState.sq8.value = 'O'
        break
      case 9:
        gameState.sq9.value = 'O'
        break
    }
  }

  checkWin()
}


function checkWin() {
  console.log('Xplayer', Xplayer)
  console.log('Oplayer', Oplayer)

  // Check for Horizontal Wins
  //Top Row
  if (Xplayer.includes(1) && Xplayer.includes(2) && Xplayer.includes(3)) {
  alert('X wins')
  gameComplete = true;
  }
  if (Oplayer.includes(1) && Oplayer.includes(2) && Oplayer.includes(3)) {
    alert('O wins')
    gameComplete = true;
  }
  //Middle Row
  if (Xplayer.includes(4) && Xplayer.includes(5) && Xplayer.includes(6)) {
    alert('X wins')
    gameComplete = true;
  }
  if (Oplayer.includes(4) && Oplayer.includes(5) && Oplayer.includes(6)) {
    alert('O wins')
    gameComplete = true;
  }
  //Bottom Row
  if (Xplayer.includes(7) && Xplayer.includes(8) && Xplayer.includes(9)) {
    alert('X wins')
    gameComplete = true;
  }
  if (Oplayer.includes(7) && Oplayer.includes(8) && Oplayer.includes(9)) {
    alert('O wins')
    gameComplete = true;
  }

  // Check for Vertical Wins
  //Left Column
  if (Xplayer.includes(1) && Xplayer.includes(4) && Xplayer.includes(7)) {
    alert('X wins')
    gameComplete = true;
  }
  if (Oplayer.includes(1) && Oplayer.includes(4) && Oplayer.includes(7)) {
    alert('O wins')
    gameComplete = true;
  }
  //Middle Column
  if (Xplayer.includes(2) && Xplayer.includes(5) && Xplayer.includes(8)) {
    alert('X wins')
    gameComplete = true;
  }
  if (Oplayer.includes(2) && Oplayer.includes(5) && Oplayer.includes(8)) {
    alert('O wins')
    gameComplete = true;
  }
  //Right Column
  if (Xplayer.includes(3) && Xplayer.includes(6) && Xplayer.includes(9)) {
    alert('X wins')
    gameComplete = true;
  }
  if (Oplayer.includes(3) && Oplayer.includes(6) && Oplayer.includes(9)) {
    alert('O wins')
    gameComplete = true;
  }

  //Check for Diagonal Wins
  //Top Left to Bottom Right
  if (Xplayer.includes(1) && Xplayer.includes(5) && Xplayer.includes(9)) {
    alert('X wins')
    gameComplete = true;
  }
  if (Oplayer.includes(1) && Oplayer.includes(5) && Oplayer.includes(9)) {
    alert('O wins')
    gameComplete = true;
  }

  //Top Right to Bottom Left
  if (Xplayer.includes(3) && Xplayer.includes(5) && Xplayer.includes(7)) {
    alert('X wins')
    gameComplete = true;
  }
  if (Oplayer.includes(3) && Oplayer.includes(5) && Oplayer.includes(7)) {
    alert('O wins')
    gameComplete = true;
  }
}

function restartGame(){
  Xplayer = []
  Oplayer = []
  gameState.sq1.value = 'G'
  gameState.sq2.value = 'G'
  gameState.sq3.value = 'G'
  gameState.sq4.value = 'G'
  gameState.sq5.value = 'G'
  gameState.sq6.value = 'G'
  gameState.sq7.value = 'G'
  gameState.sq8.value = 'G'
  gameState.sq9.value = 'G'
  gameComplete = false
  console.log('Game Restarted')

}


</script>

<template>

<button @click="player='X'">X player</button>
<button @click="player='O'">O player</button>

<h3>
  Current Player {{ player }}
</h3>

  <div id="container">
    <div id="toprow">
      <button id="sq1" @click="sqClick(1)">{{ gameState.sq1 }}</button>
      <button id="sq2" @click="sqClick(2)">{{ gameState.sq2 }}</button>
      <button id="sq3" @click="sqClick(3)">{{ gameState.sq3 }}</button>
    </div>

    <div id="midrow">
      <button id="sq4" @click="sqClick(4)">{{ gameState.sq4 }}</button>
      <button id="sq5" @click="sqClick(5)">{{ gameState.sq5 }}</button>
      <button id="sq6" @click="sqClick(6)">{{ gameState.sq6 }}</button>
    </div>

    <div id="botrow">
      <button id="sq7" @click="sqClick(7)">{{ gameState.sq7 }}</button>
      <button id="sq8" @click="sqClick(8)">{{ gameState.sq8 }}</button>
      <button id="sq9" @click="sqClick(9)">{{ gameState.sq9 }}</button>
    </div>

    <div>
      <h3 v-if="gameComplete">Game Over</h3>
      <h5 v-if="gameComplete">Press restart to play again</h5>
      <button @click="restartGame()">Restart Game</button>
    </div>

  </div>


</template>

<style scoped>

</style>
