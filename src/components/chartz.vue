<template>
<div class="">

  <div class="mark">
    <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 500 100" width="500" height="100">
    <polyline class="line color1" :points="data1"/>
    <polyline class="line color2" :points="data2"/>
    <circle class="pcolor1" v-for="x in pointsData1" :cx="x[0]" :cy="x[1]"  r="5" fill="#333" />
    <circle class="pcolor2" v-for="x in pointsData2" :cx="x[0]" :cy="x[1]"  r="5" fill="#333" />
  </svg>
  </div>

</div>
</template>

<script>
export default {
  name: 'chartz',
  props: {

  },
  data () {
    return {
      data1: ['0,50', '50,50', '100,30', '150,80', '400,20', '500,50'],
      data2: ['0,70', '40,80', '90,40', '180,90', '300,30', '500,80'],
      pointsData1: [],
      pointsData2: []
    }
  }
}
</script>

<style lang="scss" scoped>
.line {
    fill: none;
    stroke-width: 5;
    stroke-linecap: round;
    stroke-linejoin: round;
    stroke-miterlimit: 10;
    opacity: .7;
    animation-name: show;
    animation-duration: 1s;
    animation-fill-mode: backwards;
    animation-timing-function: ease-in;
    transition: 0.5s;
    perspective: 500px;
    transform-origin: 50%;
    z-index: 1;
    cursor: pointer;
    &:hover {
        // stroke: #333;
        opacity: 1;
    }
}
@keyframes show {
    from {
        opacity: 0;
    }
    to {}
}
.color1 {
    stroke: blue;
}
.pcolor1 {
    fill: blue;
}
.color2 {
    stroke: pink;
    animation-delay: 0.5s;
}
.pcolor2 {
    fill: pink;
}

.pcolor1,
.pcolor2 {
    animation-name: show;
    animation-duration: 0.5s;
    animation-delay: 1s;
    animation-fill-mode: backwards;
    animation-timing-function: ease-in;
    transition: .3s;
    transform-origin: 50%;
    opacity: .7;
    cursor: pointer;
    &:hover {
      // fill: #333;
      opacity: 1;
      transform: scale(1.5, 1.5);
    }
}

.mark {
  position: relative;
    &:before {
        content: "";
        background: #ddd;
        width: 100%;
        height: 1px;
        position: absolute;
        top: 50px;
        left: 0;
    }
}
svg {
    position: relative;
    max-width: 100%;
    height: 100px;
}
</style>
