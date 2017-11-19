<template>
<div class="container column justify-content-center align-items-center height">

  <div class="box-chartz container">
    <circleProgress percent="47" :strokeWidth="4"/>

    <circleProgress percent="69" :strokeWidth="2"/>

    <circleProgress percent="96" :strokeWidth="1" stroke="#32f4e8"/>
  </div>

   <div class="box-chartz">
    <lineProgress type="line" :stroke-width="2" :raio="4" :data="data" :height="100" :write="write"></lineProgress>
  </div>

   <div class="box-chartz">
    <verticalLine type="line" :data="dataPercent" :height="100" :write="writePercent" :columnWidth="columnWidth"></verticalLine>
  </div>


  <!-- <div class="box-chartz">
    <chartz></chartz>
  </div> -->




</div>
</template>

<script>
import chartz from '@/components/chartz'

import circleProgress from '@/components/circleProgress'
import lineProgress from '@/components/lineProgress'
import verticalLine from '@/components/verticalLine'
export default {
  components: {
    chartz,
    circleProgress,
    lineProgress,
    verticalLine
  },
  data () {
    return {
      data: [50, 20, 60, 100, 20, 40],
      write: ['Jan', 'Fev', 'Mar', 'Abr', 'Mai', 'Jun'],

      dataPercent: [50, 20, 60, 100, 20, 40],
      writePercent: ['Jan', 'Fev', 'Mar', 'Abr', 'Mai', 'Jun'],
      columnWidth: 100
    }
  }
}
</script>

<style lang="scss">
.box-chartz {
  width: 700px;
  max-width: 90%;
  margin-top: 50px;
}
.height {
  box-sizing: border-box;
  padding-top: 50px;
  padding-bottom: 50px;
}
</style>
