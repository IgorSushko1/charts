<template lang="pug">
.index
  b-button(@click="openModal") Создать график
  template(v-if="arrOfCharts.length")
    template(v-for="(chart, index) in arrOfCharts")
      Chart(:dataSource="chart")
  b-modal#modal__create-chart(hide-footer hide-header)
    Form(@getData="setChart")
</template>

<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      arrOfCharts: []
    }
  },
  methods: {
    openModal() {
      this.$bvModal.show('modal__create-chart');
    },
    setChart(data) {
      this.arrOfCharts.push(data);
      this.$bvModal.hide('modal__create-chart');
    }
  }
}
</script>

<style>
#modal__create-chart .modal-body{
  display: flex;
}
.index {
  margin: 40px;
}
</style>
