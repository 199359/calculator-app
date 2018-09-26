<!--suppress ALL -->
<template>
  <div class="calculator">
    <h1 class="display">{{current || 0}}</h1>
    <h1 @click="clear" class="btn">C</h1>
    <h1 @click="sign" class="btn">+/-</h1>
    <h1 @click="percentage" class="btn">%</h1>
    <h1 class="btn operator">/</h1>
    <h1 @click="append('7')" class="btn">7</h1>
    <h1 @click="append('8')" class="btn">8</h1>
    <h1 @click="append('9')" class="btn">9</h1>
    <h1 class="btn operator">X</h1>
    <h1 @click="append('4')" class="btn">4</h1>
    <h1 @click="append('5')" class="btn">5</h1>
    <h1 @click="append('6')" class="btn">6</h1>
    <h1 class="btn operator">-</h1>
    <h1 @click="append('1')" class="btn">1</h1>
    <h1 @click="append('2')" class="btn">2</h1>
    <h1 @click="append('3')" class="btn">3</h1>
    <h1 class="btn operator">+</h1>
    <h1 @click="append('0')" class="btn zero">0</h1>
    <h1 @click="dot" class="btn">.</h1>
    <h1 class="btn operator">=</h1>
  </div>
</template>

<script>
export default {
  data() {
    return {
      current: '12300'
    }
  },
  methods: {
    clear() {
      this.current = ''
    },
    sign() {
      this.current = this.current.charAt(0) === '-' ?
        this.current.slice(1) : `-${this.current}`
    },
    percentage() {
      this.current = this.current = `${parseFloat(this.current) / 100}`
    },
    append(number) {
      this.current = `${this.current}${number}`
    },
    dot() {
      if ( this.current.indexOf('.') === -1){
        this.append('.')
      }
    }
  }
}
</script>

<style scoped>
.calculator {
  width: 1000px;
  font-size: 40px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
}
.zero{
  grid-column: 1 /3;
}
.btn {
  background-color: #eee;
  border: 1px solid;
}
.operator {
  background-color: orange;
  color: white;
}
  .display {
    grid-column: 1 / 5;
    background-color: bisque;
  }
</style>
