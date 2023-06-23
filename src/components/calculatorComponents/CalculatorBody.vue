<template>
  <div>
    <DigitComponent @outer="numberInput('1')">1</DigitComponent>
    <DigitComponent @outer="numberInput('2')">2</DigitComponent>
    <DigitComponent @outer="numberInput('3')">3</DigitComponent>
    <DigitComponent @outer="operatorInput('+')">+</DigitComponent>
    <br>
    <DigitComponent @outer="numberInput('4')">4</DigitComponent>
    <DigitComponent @outer="numberInput('5')">5</DigitComponent>
    <DigitComponent @outer="numberInput('6')">6</DigitComponent>
    <DigitComponent @outer="operatorInput('-')">-</DigitComponent>
    <br>
    <DigitComponent @outer="numberInput('7')">7</DigitComponent>
    <DigitComponent @outer="numberInput('8')">8</DigitComponent>
    <DigitComponent @outer="numberInput('9')">9</DigitComponent>
    <DigitComponent @outer="operatorInput('*')">*</DigitComponent>
    <br>
    <DigitComponent @outer="operatorInput('C')">C</DigitComponent>
    <DigitComponent @outer="numberInput('0')">0</DigitComponent>
    <DigitComponent @outer="equalInput">=</DigitComponent>
    <DigitComponent @outer="operatorInput('/')">/</DigitComponent>
  </div>
</template>

<script>
import DigitComponent from '@/components/calculatorComponents/DigitComponent.vue'

export default {
  name: 'CalculatorBody',
  components: {
    DigitComponent
  },
  methods: {
    numberInput: function (number) {
      this.$emit('number', number)
    },
    operatorInput: function (operator) {
      this.$emit('operator', operator)
    },
    equalInput: function () {
      this.$emit('sign')
    }
  }
}
</script>
<style lang="scss">
</style>
