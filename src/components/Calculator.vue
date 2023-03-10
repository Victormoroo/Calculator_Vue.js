<template>
  <div id="calc">
    <h3><ion-icon name="calculator-outline"></ion-icon>Calculadora</h3>
    <div id="operations">
      <div id="previus-operation">{{getOperation}}</div>
      <div id="current-operation">{{getResult}}</div>
    </div>
    <div id="buttons-container">
      <button @click="clickC()" id="zero-c-btn">C</button>
      <button id="del-btn"><ion-icon name="backspace-outline" @click="clickDel()"></ion-icon></button>
      <button @click="click('÷')">÷</button>
      <button class="number" @click="click('7')">7</button>
      <button class="number" @click="click('8')">8</button>
      <button class="number" @click="click('9')">9</button>
      <button @click="click('*')">x</button>
      <button class="number" @click="click('4')">4</button>
      <button class="number" @click="click('5')">5</button>
      <button class="number" @click="click('6')">6</button>
      <button @click="click('-')">-</button>
      <button class="number" @click="click('1')">1</button>
      <button class="number" @click="click('2')">2</button>
      <button class="number" @click="click('3')">3</button>
      <button @click="click('+')">+</button>
      <!-- <button @click="click('%')">%</button> -->
      <button class="number" id="zero-c-btn" @click="click('0')">0</button>
      <button class="number" @click="click('.')">.</button>
      <button id="equal-btn" @click="clickResult()">=</button>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Calculator',

    data() {
      return {
        getOperation: '',
        getResult: '0',
      }
    },

    methods: {
      clickC() {
        this.getResult = '0';
        this.getOperation = '';
      },

      clickDel() {
        if (this.getResult.length > 1) {
          this.getResult = this.getResult.substring(0, this.getResult.length - 1);
        }
        else {
          this.getResult = '0';
        }
      },

      click(number) {
        if(this.getResult == '0') {
          this.getResult = number;
        }
        else {
          this.getResult += number;
        }
      },

      clickResult() {
        let operation = this.getResult;
        this.getOperation = operation;

        operation = operation.replace('x', '*');
        operation = operation.replace('÷', '/');

        this.getResult = eval(operation);
      }
    }
  }
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');

  * {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
    font-family: 'Roboto', sans-serif;
  }

  body {
    height: 100vh;
    background-color: #333333;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  #calc {
    width: 22rem;
    padding: .5rem;
    background-color: #202020;
    color: #ffffff;
    display: flex;
    flex-direction: column;
    border-radius: 10px;
  }

  #calc ion-icon,
  #calc h3 {
    color: #dfdfdf;
  }

  #calc ion-icon {
    font-size: 1.4rem;
    margin-right: 0.3rem;
  }

  #calc h3 {
    font-size: .8rem;
    font-weight: 300;
    display: flex;
    align-items: center;
  }

  #operations {
    text-align: right;
  }

  #previus-operation,
  #current-operation {
    padding: 0.2rem;
    overflow-wrap: break-word;
    min-height: 3.2rem;
  }

  #previus-operation {
    color: #a6a6a6;
    margin-bottom: -1.5rem;
  }

  #current-operation {
    font-size: 2rem;
    font-weight: 600;
    margin-bottom: 0.2rem;
  }

  #buttons-container {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr;
    gap: 3px
  }

  #buttons-container button {
    border: 1px solid transparent;
    border-radius: 9px;
    height: 4.8rem;
    font-size: 1.2rem;
    background-color: #2b2b2b;
    cursor: pointer;
    color: #ffffff;
    font-weight: 500;
    font-size: 1.7rem;
  }

  #buttons-container .number {
    background-color: #3b3b3b;
  }

  #buttons-container .number:hover,
  #buttons-container button:hover:active {
    background-color: #2b2b2b;
  }

  #buttons-container .number:hover:active {
    background-color: #282828;
  }

  #buttons-container button:hover {
    background-color: #3b3b3b;
  }

  #buttons-container #del-btn ion-icon{
    color: #ffffff;
    font-size: 2.2rem;
    display: flex;
    margin: 0 auto;
  }

  #buttons-container #zero-c-btn {
    grid-column: span 2;
  }

  #buttons-container #equal-btn,
  #buttons-container #equal-btn:hover:active {
    background-color: #3c90d4;
  }

  #buttons-container #equal-btn:hover {
    background-color: #2f7cbc;
  }
</style>