<template>
  <v-chart class="chart" :option="option" />
</template>

<script>
import { use } from "echarts/core";
import { CanvasRenderer } from "echarts/renderers";
import { PieChart } from "echarts/charts";
import {
  TitleComponent,
  TooltipComponent,
  LegendComponent
} from "echarts/components";
import VChart, { THEME_KEY } from "vue-echarts";
import { ref, defineComponent } from "vue";

use([
  CanvasRenderer,
  PieChart,
  TitleComponent,
  TooltipComponent,
  LegendComponent
]);

export default defineComponent({
  name: "HelloWorld",
  components: {
    VChart
  },
  provide: {
    [THEME_KEY]: "clear"
  },
  setup () {
    const option = ref({
      title: {
        text: "Atendimento",
        left: "center"
      },
      tooltip: {
        trigger: "item",
        formatter: "{a} <br/>{b} : {c} ({d}%)"
      },
      legend: {
        orient: "vertical",
        left: "left",
        data: ["Amanda", "Helton", "Eron", "Henrique", "João Paulo","Jullyadson","Ewerton", "Clederson", "Pedro",]
      },
      series: [
        {
          name: "Traffic Sources",
          type: "pie",
          radius: "55%",
          center: ["50%", "50%"],
          data: [
            { value: 335, name: "Amanda" },
            { value: 310, name: "Helton" },
            { value: 5000, name: "Eron" },
            { value: 135, name: "Henrique" },
            { value: 1548, name: "João Paulo" },
            { value: 1338, name: "Jullyadson" },
            { value: 5000, name: "Ewerton" },
            { value: 135, name: "Cledersonz" },
            { value: 1548, name: "Pedro" },
          ],
          emphasis: {
            itemStyle: {
              shadowBlur: 10,
              shadowOffsetX: 0,
              shadowColor: "rgba(0, 0, 0, 0.5)"
            }
          }
        }
      ]
    });

    return { option };
  }
});
</script>

<style scoped>
.chart { 
  width: 100%;
  height: 300px;
}
</style>