<template>
  <div id="app">
    <div class="game">
      <div class="game-board">
        <div className="board-row">
          <button type="button" class="square" @click="handleClick(0)"></button>
          <button type="button" class="square" @click="handleClick(1)"></button>
          <button type="button" class="square" @click="handleClick(2)"></button>
        </div>
        <div className="board-row">
          <button type="button" class="square" @click="handleClick(3)"></button>
          <button type="button" class="square" @click="handleClick(4)"></button>
          <button type="button" class="square" @click="handleClick(5)"></button>
        </div>
        <div className="board-row">
          <button type="button" class="square" @click="handleClick(6)"></button>
          <button type="button" class="square" @click="handleClick(7)"></button>
          <button type="button" class="square" @click="handleClick(8)"></button>
        </div>

        <!-- Board -->
        <!-- <board
          :squares="squares"
          @click="{ i => handleClick(i) }"
        /> -->
      </div>
      <div class="game-info">
        <!-- Status -->
        <!-- Moves -->
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
// import Board from './components/Board.vue'

@Component({
  components: {
    // 'board': Board,
  },
})
export default class App extends Vue {
  public handleClick(i: Number): void {
    console.log('handleClick', i);
  }
}
</script>

<style>
  body {
    font: 14px "Century Gothic", Futura, sans-serif;
    margin: 20px;
  }
  ol, ul {
    padding-left: 30px;
  }
  .board-row:after {
    clear: both;
    content: "";
    display: table;
  }
  .status {
    margin-bottom: 10px;
  }
  .square {
    background: #fff;
    border: 1px solid #999;
    float: left;
    font-size: 24px;
    font-weight: bold;
    line-height: 34px;
    height: 34px;
    margin-right: -1px;
    margin-top: -1px;
    padding: 0;
    text-align: center;
    width: 34px;
  }
  .square:focus {
    outline: none;
  }
  .kbd-navigation .square:focus {
    background: #ddd;
  }
  .game {
    display: flex;
    flex-direction: row;
  }
  .game-info {
    margin-left: 20px;
  }
</style>
