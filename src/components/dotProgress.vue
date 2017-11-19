<template>
<div>

  <div v-if="type == 'line'" class="mark" style="width: 100%; max-width: 100%">
    <svg xmlns="http://www.w3.org/2000/svg" class="mark" xmlns:xlink="http://www.w3.org/1999/xlink" :viewBox="'-60 -25 ' + (dataSize - 1) * (height + 20) + ' ' + (height + 60)" :style="{ strokeWidth: strokeWidth }">

      <text v-for="(write, index) in (height / 10) + 1" :y="index * 10" :x="-30" class="text-write">
        {{(write * 10 - 10) * -1 + 100}}
      </text>


        <!-- horizontal -->
        <line v-for="(write, index) in height / 10" x1="86%" :x2="0" :y1="index * 10" :y2="index * 10" fill="red" style="stroke: #ddd; stroke-width: .5px;"/>
        <!-- horizontal -->
        <!-- marcao horicontal -->
        <line v-for="(line, index) in pointsData" x1="86%" :x2="0" :y1="line[1]" :y2="line[1]" style="stroke: #ccc; stroke-width: 1px;"/>
        <!-- marcao horicontal -->

        <line v-for="(write, index) in height / 10" :x1="index * 100" :x2="index * 100" :y1="0" :y2="100" fill="red" style="stroke: #ddd; stroke-width: .5px;"/>
        <line x1="86%" x2="0" y1="100" y2="100" style="stroke: #ddd; stroke-width: .5px;"/>

        <!-- escrita em baixo -->
        <text v-for="(valueWrite, index) in write" :x="index * 100" :y="120" class="text-write">
          {{valueWrite}}
        </text>
        <!-- escrita em baixo -->

        <!-- grafico -->

        <g class="point-show" v-for="x in pointsData">
          <circle class="ball-over pcolor1" :cx="x[0]" :cy="x[1]" :r="raio" fill="#333"/>
          <text class="show-text text-value" :x="x[0]" :y="x[1]">{{100 - x[1]}}</text>
        </g>

        <!-- grafico -->
      </g>

    </svg>

  </div>
  <!-- <div class="container align-items-center justify-content-between">
    <div class="write container flex-grow-1" v-for="y in write">
        {{y}}
    </div>
  </div> -->

</div>
</template>

<script>
export default {
  name: 'chartz',
  props: {
    type: {
      type: String
    },
    data: {
      type: Array,
      default: []
    },
    write: {
      type: Array,
      default: []
    },
    height: {
      type: Number
    },
    size: {
      type: Number
    },
    strokeWidth: {
      type: Number,
      default: 1
    },
    raio: {
      type: Number,
      default: 2
    }
  },

  data () {
    return {
      pointsData: [],
      line: [],
      dataSize: 0,
      fullData: [],
      reverseFullData: []
    }
  },
  created () {
    this.dataSize = this.data.length
    console.log('size: ' + this.dataSize)

    let quociente = (this.dataSize * 100) / (this.dataSize)

    for (let i = 0; i < this.dataSize; i++) {
      this.fullData.push(`${quociente * i},${100 - this.data[i]}`)
    }

    this.fullData.map((data, index) => {
      this.pointsData.push(data.split(','))
      console.log(this.pointsData[index])
    })
  }

}
</script>

<style lang="scss" scoped>
.show-text {
  // display: none;
}
.point-show {
  width: 40px;
  height: 40px;
  background: red;
  fill: red;
  &:hover {
    .show-text {
      display: block
    }
  }
}



.text-value,
.text-write {
    font-size: 10px;
    fill: #b8b8b8;
    transition: 0.3s;
    text-align: center;

    &:hover {
        fill: #333;
    }
}
.text-write {}
.text-value {
    transform: translate(-5px, -10px);
}
.write {
    background: red;
    text-align: center;
    border: 1px solid blue;
}
.line {
    fill: none;
    // stroke-width: 1;
    stroke-linecap: round;
    stroke-linejoin: round;
    stroke-miterlimit: 10;
    animation-name: show;
    animation-duration: 1s;
    animation-fill-mode: backwards;
    animation-timing-function: ease-in;
    transition: 0.5s;
    transform-origin: center center;
    z-index: 1;
    cursor: pointer;
    &:hover {}
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
    stroke: #fff;
    stroke-width: 2px
}

.pcolor1 {
    animation-name: show;
    animation-duration: 0.5s;
    animation-delay: 1s;
    animation-fill-mode: backwards;
    animation-timing-function: ease-in;
    transition: 0.1s;
    transform-origin: 50%;
    cursor: pointer;
    &:hover {
        transform: scale(1.5, 1.5);
    }
}

.mark {
    position: relative;
    overflow: hidden;
    // &:before {
    //     content: "";
    //     background: #ddd;
    //     width: 100%;
    //     height: 1px;
    //     position: absolute;
    //     top: 50%;
    //     left: 0;
    // }
}
svg {
    position: relative;
    width: 100%;
    transition: 0.5s;
    cursor: pointer;
    border: 1px solid #ddd;
}
</style>
