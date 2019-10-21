<template>
  <ol>
    <li
      v-for="(_, move) in history"
      :key="move"
      >
      <button @click="() => jumpTo(move)">
        {{ desc(move) }}
      </button>
    </li>
  </ol>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import { Squares } from '../App.vue';

@Component
export default class Moves extends Vue {
  @Prop() public history!: Squares[];
  @Prop() public jumpTo!: () => void;
  public desc(move: number) {
    return move ?
      'Go to move #' + move
      : 'Go to game start';
  }
}
</script>

<style scoped>
  ol, ul {
    padding-left: 30px;
  }
</style>
