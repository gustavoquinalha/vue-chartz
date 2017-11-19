<template>
<div>

    <div class="relative">
      <div class="abs">
        <svg viewBox="0 0 36 36" width="200" height="200" class="circular-chart" :style="{strokeWidth: strokeWidth}">
          <path y="100" class="circle-full" d="M18 2.0845 a 15.9155 15.9155 0 0 1 0 31.831 a 15.9155 15.9155 0 0 1 0 -31.831" />
          <path y="100" class="circle" :stroke="stroke" :stroke-dasharray="percent + ', 100'" d="M18 2.0845 a 15.9155 15.9155 0 0 1 0 31.831 a 15.9155 15.9155 0 0 1 0 -31.831" />
        </svg>
      </div>
      <div class="quatity">
        <div class="">
          {{percent + '%'}}
        </div>
      </div>
    </div>

</div>
</template>

<script>
export default {
  name: 'chartz',

  props: {
    stroke: {
      type: String,
      default: '#2C00FC'
    },
    percent: {
      type: String
    },
    strokeWidth: {
      type: Number,
      default: 3
    }
  },

  data () {
    return {
      pointsData: [],
      line: [],
      teste: 0
    }
  },

  mounted () {
  }

}
</script>

<style lang="scss" scoped>
.relative {
  position: relative;
  overflow: hidden;
}
.circular-chart {
  width: 100%;
  display: block;
  margin: 10px auto;
  // max-width: 80%;
  // max-height: 250px;
}
.quatity {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-pack: center;
      -ms-flex-pack: center;
          justify-content: center;
  -webkit-box-align: center;
      -ms-flex-align: center;
          align-items: center;
  -webkit-animation: progressbg 1s 1s ease-out backwards;
          animation: progressbg 1s 1s ease-out backwards;
  cursor: pointer;
  -webkit-transition: .1s;
  transition: .1s;
  &:hover {
    -webkit-transform: scale(1.5, 1.5);
            transform: scale(1.5, 1.5);
  }
}

.circle {
  fill: none;
  stroke-linecap: round;
  -webkit-animation: progress 1s 1s ease-out backwards;
          animation: progress 1s 1s ease-out backwards;
  -webkit-transition: .5s;
  transition: .5s;
  position: relative;
  background: red;
  z-index: 2;
}
.circle-full {
  stroke: #ddd;
  fill: none;
  stroke-linecap: round;
  -webkit-transition: .5s;
  transition: .5s;
  -webkit-animation: progressbg 1s ease-out forwards;
          animation: progressbg 1s ease-out forwards;
  z-index: 1;
}
@-webkit-keyframes progressbg {
  0% {
    opacity: 0
  }
}
@keyframes progressbg {
  0% {
    opacity: 0
  }
}
@-webkit-keyframes progress {
  0% {
    stroke-dasharray: 0 100;
  }
}
@keyframes progress {
  0% {
    stroke-dasharray: 0 100;
  }
}







//
// svg {
//     position: relative;
//     width: 100%;
//     -webkit-transition: .5s;
//     transition: .5s;
//     cursor: pointer;
// }
</style>
