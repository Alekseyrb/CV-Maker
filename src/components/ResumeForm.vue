<template>
  <form class="card card-w30" @submit.prevent="subForm">
    <div class="form-control">
      <label for="type">Тип блока</label>
      <select id="type" v-model="type">
        <option value="title">Заголовок</option>
        <option value="subtitle">Подзаголовок</option>
        <option value="avatar">Аватар</option>
        <option value="text">Текст</option>
      </select>
    </div>

    <div class="form-control">
      <label for="value">Значение</label>
      <textarea
          id="value"
          rows="3"
          v-model="valueInput"
      ></textarea>
    </div>

    <button class="btn primary" :disabled="valueInput.length < 3">Добавить</button>
  </form>
</template>

<script>
export default {
  name: "ResumeForm",
  data() {
    return {
      type: 'title',
      valueInput: '',
    }
  },
  props: {
    bloc: {
      type: Array,
      required: true,
    }
  },
  methods: {
    subForm() {
      this.bloc.push({
        'type': this.type,
        'value': this.valueInput,
      });
      console.log(this.type, this.valueInput, this.bloc);
      this.type = 'title';
      this.valueInput = '';
    }
  },
}
</script>

<style scoped>

</style>