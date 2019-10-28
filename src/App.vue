<template>
  <div id="app">
    <div class="game">
      <board
        :squares="currentHistory"
        :handleClick="i => handleClick(i)"
      />
      <div class="game-info">
        <div>{{ status }}</div>
        <moves
          :history="history"
          :jumpTo="(move) => jumpTo(move)"
        />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Board from './components/Board.vue';
import Moves from './components/Moves.vue';

export interface History {
  [index: number]: Squares;
}

export interface Squares {
  [index: number]: null | string;
}

@Component({
  components: {
    Board,
    Moves,
  },
})
export default class App extends Vue {
  public history: Squares[] = [ Array(9).fill(null) ];
  public stepNumber: number = 0;
  public xIsNext: boolean = false;

  get currentHistory() {
    return this.history[this.stepNumber];
  }

  get status() {
    const winner = this.calculateWinner(this.currentHistory);
    if (winner) {
      return `Winner:  ${winner}`;
    }
    return `Next player:  ${(this.xIsNext ? 'X' : 'O')}`;
  }

  public handleClick(i: number): void {
    const history = this.history.slice(0, this.stepNumber + 1);
    const squares = history[history.length - 1].slice();

    if (squares[i] || this.calculateWinner(squares)) {
      return;
    }

    squares[i] = this.xIsNext ? 'X' : 'O';
    this.history = history.concat([ squares ]);
    this.stepNumber = this.history.length - 1;
    this.xIsNext = !this.xIsNext;
  }

  public jumpTo(move: number): void {
    this.stepNumber = move;
    this.xIsNext = move % 2 === 1;
  }

  private calculateWinner(squares: Squares) {
    const lines = [
      [0, 1, 2],
      [3, 4, 5],
      [6, 7, 8],
      [0, 3, 6],
      [1, 4, 7],
      [2, 5, 8],
      [0, 4, 8],
      [2, 4, 6],
    ];

    for (const line of lines) {
      const [a, b, c] = line;
      if (squares[a]
        && squares[a] === squares[b]
        && squares[a] === squares[c]) {
        return squares[a];
      }
    }

    return null;
  }

}
</script>

<style>
  body {
    font: 14px "Century Gothic", "Futura", "sans-serif";
    margin: 20px;
  }
  .status {
    margin-bottom: 10px;
  }
  .game {
    display: flex;
    flex-direction: row;
  }
  .game-info {
    margin-left: 20px;
  }
</style>
