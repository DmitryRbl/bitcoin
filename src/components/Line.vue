<template>
    <LineChartGenerator
      :chart-options="chartOptions"
      :chart-data="chartData"
      :chart-id="chartId"
      :dataset-id-key="datasetIdKey"
      :plugins="plugins"
      :css-classes="cssClasses"
      :styles="styles"
      :width="width"
      :height="height"
    />
</template>

<script>
import { Line as LineChartGenerator } from 'vue-chartjs/legacy'

import {
Chart as ChartJS,
Title,
Tooltip,
Legend,
LineElement,
LinearScale,
CategoryScale,
PointElement
} from 'chart.js'

ChartJS.register(
Title,
Tooltip,
Legend,
LineElement,
LinearScale,
CategoryScale,
PointElement
)

export default {
name: 'LineChart',
components: {
    LineChartGenerator
},
props: {
    chartId: {
    type: String,
    default: 'line-chart'
    },
    datasetIdKey: {
    type: String,
    default: 'label'
    },
    width: {
    type: Number,
    default: 400
    },
    height: {
    type: Number,
    default: 600
    },
    cssClasses: {
    default: '',
    type: String
    },
    styles: {
    type: Object,
    default: () => {}
    },
    plugins: {
    type: Array,
    default: () => []
    }
},
data() {
    return {
    chartData: {
        datasets: [
        {
            label: 'Data One',
            backgroundColor: '#f87979',
            data: [{x: '0', y: 20}, {x: '1', y: 10}, {x: '5', y: 10}]
        }
        ]
    },
    chartOptions: {
        responsive: true,
        maintainAspectRatio: false
    }
    }
}
}
</script>
  