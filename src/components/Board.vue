<template>
  <div class="game-board">
    <div class="board-row">
      <square :value="squares[0]" :handleClick="() => handleClick(0)" />
      <square :value="squares[1]" :handleClick="() => handleClick(1)" />
      <square :value="squares[2]" :handleClick="() => handleClick(2)" />
    </div>
    <div class="board-row">
      <square :value="squares[3]" :handleClick="() => handleClick(3)" />
      <square :value="squares[4]" :handleClick="() => handleClick(4)" />
      <square :value="squares[5]" :handleClick="() => handleClick(5)" />
    </div>
    <div class="board-row">
      <square :value="squares[6]" :handleClick="() => handleClick(6)" />
      <square :value="squares[7]" :handleClick="() => handleClick(7)" />
      <square :value="squares[8]" :handleClick="() => handleClick(8)" />
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import { Squares } from '../App.vue';
import Square from './Square.vue';

@Component({
  components: {
    Square,
  },
})
export default class Board extends Vue {
  @Prop() public squares!: Squares;
  @Prop() public handleClick!: () => void;
}
</script>

<style scoped>
  .board-row:after {
    content: "";
    display: table;
    clear: both;
  }
</style>
