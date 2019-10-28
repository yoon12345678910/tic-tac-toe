<template>
  <button
    @click="handleClick"
    type="button"
    class="square"
  >
    {{ value }}
  </button>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component
export default class Square extends Vue {
  @Prop() public value!: string;
  @Prop() public handleClick!: () => void;
}
</script>

<style scoped>
  .square {
    padding: 0;
    margin-right: -1px;
    margin-top: -1px;
    width: 34px;
    height: 34px;
    border: 1px solid #999;
    background: #fff;
    float: left;
    font-size: 24px;
    font-weight: bold;
    line-height: 34px;
    text-align: center;
  }
  .square:focus {
    outline: none;
  }
</style>
