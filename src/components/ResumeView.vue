<template>
  <div class="card card-w70">

    <div v-if="blocs.length">
        <component
            v-for="bloc in blocs"
            :is="'resume-' + bloc.type"
            v-bind="{value: bloc.value}"
        ></component>
    </div>
    <h3 v-else>Добавьте первый блок, чтобы увидеть результат</h3>
  </div>


</template>

<script>
import ResumeAvatar from "@/components/parts/ResumeAvatar.vue";
import ResumeSubtitle from "@/components/parts/ResumeSubtitle.vue";
import ResumeText from "@/components/parts/ResumeText.vue";
import ResumeTitle from "@/components/parts/ResumeTitle.vue";

export default {
  name: "ResumeView",
  props: {
    blocs: {
      type: Array,
      required: true,
    }
  },
  components: {
    ResumeText,
    ResumeAvatar,
    ResumeTitle,
    ResumeSubtitle,
  }
}
</script>

<style scoped>

</style>