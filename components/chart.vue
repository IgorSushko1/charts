<template lang="pug">
.container
  #chart
    DxChart(
      id="chart"
      :data-source="dataSource"
      palette="Ocean")
      DxSeries(
        argument-field="Дата"
        value-field="Процент"
      )
      DxMargin( :bottom="40")
      DxLegend(
        vertical-alignment="bottom"
        horizontal-alignment="center"
        item-text-position="bottom"
        title="Проценты"
        )
      DxTitle( text="Заголовок графика")
        DxSubtitle( text="Подзаголовок графика")
      DxTooltip( :enabled="true" :customize-tooltip="customizeTooltip")
</template>

<script>
import {
  DxChart,
  DxSeries,
  DxMargin,
  DxLegend,
  DxTitle,
  DxSubtitle,
  DxTooltip,
} from 'devextreme-vue/chart';
import DxSelectBox from 'devextreme-vue/select-box';

export default {
  name: "Chart",
  props: ['dataSource'],
  data() {
    return {
      types: ['line', 'stackedline', 'fullstackedline'],
      type: 'line',
    }
  },
  components: {
    DxChart,
    DxSeries,
    DxMargin,
    DxLegend,
    DxTitle,
    DxSubtitle,
    DxTooltip,
  },
  methods: {
    customizeTooltip(pointInfo) {
      return {
        html: `<div><div>Дата: ${new Date(pointInfo.argument).toLocaleDateString('ru-RU')}</div><div>Процент: ${pointInfo.value}</div></div>`,
      };
    },
  }
}
</script>

<style scoped>

</style>
