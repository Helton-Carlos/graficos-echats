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
  name: "Tabela",
  components: {
    VChart
  },
  provide: {
    [THEME_KEY]: "dark"
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
        data: ["Area1", "Area2", "Area3", "Area4", "Area5"]
      },
      series: [
        {
          name: "Traffic Sources",
          type: "pie",
          radius: "55%",
          center: ["50%", "50%"],
          data: [
            { value: 335, name: "Area1" },
            { value: 310, name: "Area2" },
            { value: 500, name: "Area3" },
            { value: 135, name: "Area4" },
            { value: 1548, name: "Area5" }
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