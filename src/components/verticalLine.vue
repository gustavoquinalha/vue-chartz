<template>
<div>

  <div class="mark" style="width: 100%; max-width: 100%">
    <svg xmlns="http://www.w3.org/2000/svg" class="mark" xmlns:xlink="http://www.w3.org/1999/xlink" :viewBox="'-60 -25 ' + (dataSize - 1) * (height + 20) + ' ' + (height + 60)" :style="{ strokeWidth: strokeWidth }">


      <line x1="86%" x2="0" y1="100" y2="100" style="stroke: #ddd; stroke-width: .5px;"/>
      <line v-for="(horizontal, index) in height / 10" x1="86%" :x2="0" :y1="index * 10" :y2="index * 10" fill="red" style="stroke: #ddd; stroke-width: .5px;"/>

      <!-- escrita em baixo -->
      <text v-for="(valueWrite, index) in writePercent" :x="index * 100" :y="120" class="text-write">
        {{valueWrite}}
      </text>
      <!-- escrita em baixo -->

      <g>
        <rect v-for="(x, index) in data" :width="columnWidth - 20 + 'px'" :height="x" style="fill:blue" :x="index * columnWidth"/>
      </g>



    </svg>

  </div>

</div>
</template>

<script>
export default {
  name: 'chartz',
  props: {
    data: {
      type: Array,
      default: []
    },
    height: {
      type: Number
    },
    columnWidth: {
      type: Number
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

svg {
    position: relative;
    width: 100%;
    transition: 0.5s;
    cursor: pointer;
    border: 1px solid #ddd;
}
</style>
