<template>
  <div class="container column">
    <ResumeForm
        :bloc="blocs"
    />
    <ResumeView
        :blocs="blocs"
    />
  </div>
  <div class="container">
    <AppLoader v-if="loading"/>
    <ResumeComments
        v-else
        :comments="comments"
        @load-comment="loadComment"
    />
  </div>
</template>

<script>
import ResumeForm from "@/components/ResumeForm.vue";
import ResumeView from "@/components/ResumeView.vue";
import ResumeComments from "@/components/ResumeComments.vue";
import AppLoader from "@/components/AppLoader.vue";

export default {
  data() {
    return {
      blocs: [],
      loading: false,
      comments: [],
    }
  },
  methods: {
    async loadComment() {
      this.loading = true;
      const response = await fetch('https://jsonplaceholder.typicode.com/comments?_limit=42');
      this.comments = await response.json();
      console.log(this.comments);
      this.loading = false;
    }
  },
  components: {
    ResumeForm,
    ResumeView,
    ResumeComments,
    AppLoader,
  }
}
</script>

<style scoped>

</style>
