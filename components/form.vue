<template lang="pug">
.form
  h1 Создать график
  form(v-model="formData")
    select(v-model="formData.type")
      option(value="linearTitle") Выберите тип графика
      option(value="linear") Линейный
    select(v-model="formData.link")
      option(value="linkTitle") Выберите источник данных
      option(value="https://run.mocky.io/v3/92a0a266-0321-4ff5-9993-b394d03ceee2") Данные по ссылке
    b-button(@click.prevent="saveData") Создать график
</template>

<script>
export default {
  name: "Form",
  data() {
    return {
      formData: {type: 'linearTitle',
        link: 'linkTitle'},
    }
  },
  methods: {
    saveData() {
      if (this.formData.link !== 'linearTitle' && this.formData.type !== 'linkTitle') {
        const myRequest = new Request(this.formData.link);
        fetch(myRequest, {
          method: 'GET'}).then((response) => {
          return response.json()
        }).then(response => {
          this.$emit('getData', response);
        })
      }
    }
  }
}
</script>

<style scoped>
.form {
  display: flex;
  flex-wrap: wrap;
  width: 100%;
}
.form h1 {
  font-size: 24px;
  margin-bottom: 40px;
}
.form select {
  width: 100%;
  margin-bottom: 40px;
}
</style>
