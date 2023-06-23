<template>
  <div style="display: inline">
    <span class="dot" @click="outer"><slot></slot></span>
  </div>
</template>

<script>
/* Components render based on the rendering rules for HTML.
If your component's root tag is a block element, then it will be rendered on the next line.
If it is an inline element, then it will be rendered inline.

<div></div> is a block element by default while <span></span> is a inline element by default.
It is also why dot class's display should be inline-block in order to show circle shape.
As a result, the root tag should be set as 'display:inline' to show the component in a line. **/

export default {
  name: 'DigitComponent',
  methods: {
    outer: function () {
      this.$emit('outer')
    }
  }
}
</script>

<style type="scss">

.dot {
  height: 50px;
  width: 50px;
  border-radius: 50%;
  background-color: #d7d5d5;
  margin: 2px 2px;
  display: inline-block;
  text-align: center;
  line-height: 50px;
  font-size: 30px;
  cursor: pointer;
  color: black;
}

.dot:active{
  background-color: #48abe0;
  color: white;
  /* transform: translateY(2px); */
  transform: scale(0.9, 0.9);
}
</style>
