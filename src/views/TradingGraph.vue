<template>
    <div class="outer" style="height:100%; width: 100%; border:1px solid black">
        <TradingGraph />
    </div>
</template>
  
<script>
import TradingGraph from '../components/TradingGraph.vue'

export default {
name: 'App',
    components: {
        TradingGraph
    }
}
</script>

<style>
.outer:before {
  content: '';
  display: inline-block;
  height: 100%;
  vertical-align: middle;
}

.inner {
  display: inline-block;
  vertical-align: middle;
}

/* добавим горизонтальное центрирование */
.outer {
    display: flex;
    justify-content: center; /*Центрирование по горизонтали*/
    align-items: center;     /*Центрирование по вертикали */
}
</style>