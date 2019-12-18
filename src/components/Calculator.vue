<template>
  <div class="calculator">
    <div class="display2">{{previous || 0}}</div>
    <div class="display">{{current || 0}}</div>
    <div @click="clear" class="btn">C</div>
    <div @click="minus" class="btn">+/-</div>
    <div @click="percentage" class="btn">%</div>
    <div class="btn operator">/</div>
    <div @click="numbers(7)" class="btn">7</div>
    <div @click="numbers(8)" class="btn">8</div>
    <div @click="numbers(9)" class="btn">9</div>
    <div class="btn operator">*</div>
    <div @click="numbers(4)" class="btn">4</div>
    <div @click="numbers(5)" class="btn">5</div>
    <div @click="numbers(6)" class="btn">6</div>
    <div class="btn operator">-</div>
    <div @click="numbers(1)" class="btn">1</div>
    <div @click="numbers(2)" class="btn">2</div>
    <div @click="numbers(3)" class="btn">3</div>
    <div @click="add" class="btn operator">+</div>
    <div @click="numbers(0)" class="btn zero">0</div>
    <div class="btn">.</div>
    <div class="btn operator">=</div>
  </div>
</template>

<script>
import {} from "http";
export default {
  data() {
    return {
      current: "",
      operator: null
    };
  },

  methods: {
    clear() {
      this.current = "";
      this.previous = "";
      this.operator  = "";
    },
    numbers(number) {
      this.current = `${this.current}${number}`;
      //need to add some functionality to add new numbers, should use one method rather than 9 for each number i think?
    },
    minus() {
      this.current =
        this.current.charAt(0) === "-"
          ? this.current.slice(1)
          : `-${this.current}`;
      this.operator = "-";
    },
    percentage() {
      this.current = `${parseFloat(this.current) / 100}`;
    },
    add() {
      if (this.previous ==='') 
      {
      this.previous = this.current;}
      else
      { 
       this.previous = `${this.previous}${this.operator}${this.current}`;
      }
      this.current = "";
      this.operator = "+";
    },
    equals() {


    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.calculator {
  width: 400px;
  margin: 0 auto;
  font-size: 40px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
}

.display {
  font-size: 40px;
  grid-column: 1 / 5;
  background-color: black;
  color: white;
}

.display2 {
  font-size: 20px;
  grid-column: 1/5;
  background-color: black;
  color: white;
}

.zero {
  grid-column: 1/3;
}

.btn {
  background-color: #eee;
  border: 1px solid black;
}

.operator {
  background-color: darkorange;
  color: white;
}
</style>
