<template>
  <div class="card card-w70">
      <component :is="block.type" :content="block.content" v-for="block in blocks" :key="block.id"></component>
      <h3 v-if="blocks.length === 0">Добавьте первый блок, чтобы увидеть результат</h3>
    </div>
</template>

<script>
import ResumeAvatar from './ResumeAvatar.vue'
import ResumeSubtitle from './ResumeSubtitle.vue'
import ResumeText from './ResumeText.vue'
import ResumeTitle from './ResumeTitle.vue'
export default {
  props: ['blocks'],
  components: { ResumeTitle, ResumeSubtitle, ResumeAvatar, ResumeText },
  
}
</script>

<style>

</style>