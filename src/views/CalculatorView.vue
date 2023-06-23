<template>
  <div class="wrapper">
    <span class="rec">{{ numberStr }}</span>
     <span class="blank"></span>
     <span class="caculatorbody"></span>
     <CalculatorBody @number="editNumber" @operator = "operatorFunction" @sign="cal"/>
    </div>
</template>

<script>
import CalculatorBody from '@/components/calculatorComponents/CalculatorBody.vue'

export default {
  name: 'CalculatorView',
  components: {
    CalculatorBody
  },
  data () {
    return {
      numberStr: '0',
      currentOperator: '',
      digitAfterOperator: false,
      lastNumberStr: ''
    }
  },
  methods: {
    editNumber: function (number) {
      if (this.numberStr === '0' || this.digitAfterOperator === true) {
        const lastNumberStr = this.numberStr
        this.lastNumberStr = lastNumberStr
        this.numberStr = ''
      }
      this.numberStr += number
      this.digitAfterOperator = false
    },
    operatorFunction: function (operator) {
      switch (operator) {
        case 'C':
          this.numberStr = '0'
          break
        case '+':
        case '-':
        case '*':
        case '/':
          this.currentOperator = operator
          this.digitAfterOperator = true
      }
    },
    cal: function () {
      let calResult = 0
      const num1 = Number(this.lastNumberStr)
      const num2 = Number(this.numberStr)
      switch (this.currentOperator) {
        case '+':
          calResult = num1 + num2
          break
        case '-':
          calResult = num1 - num2
          break
        case '*':
          calResult = num1 * num2
          break
        case '/':
          calResult = num1 / num2
          break
      }
      this.numberStr = calResult.toString()
    }
  }
}
</script>

<style lang="scss">
.rec{
  height: 50px;
  width: 260px;
  border-radius: 10%;
  background-color: #000;
  margin: 2px 2px;
  display: inline-block;
  text-align: right;
  line-height: 50px;
  font-size: 30px;
  color: white;
}
.blank{
  height: 10px;
  width: 260px;
  display: block;
}
.wrapper {
  position: relative;
}
.caculatorbody{
  position: absolute;
  height: 280px;
  width: 260px;
  top: 6%;
  left: 0;
  bottom: 0;
  right: 0;
  margin: auto;
  border-radius: 0 0 10% 10%;
  background-color: rgb(69, 69, 214);
  display: inline-block;
  z-index: -1;
}
</style>
