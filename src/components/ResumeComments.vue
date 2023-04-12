<template>
  <p>
    <button class="btn primary" @click="loadComment">Загрузить комментарии</button>
  </p>
  <div class="card">
    <h2>Комментарии</h2>
    <ul class="list">
      <li class="list-item" v-for="comment in comments" :key="comment.id">
        <div>
          <p><strong>{{ comment.email }}</strong></p>
          <small>{{ comment.body }}</small>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "ResumeComments",
  emits: ['load-comment'],
  props: {
    comments: Array,
  },
  methods: {
    loadComment() {
      this.$emit('load-comment');
    }
  }
}
</script>

<style scoped>

</style>