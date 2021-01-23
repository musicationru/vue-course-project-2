<template>
  <div class="container column">
    <app-form
      v-model:type="type"
      v-model:content.trim="content"
      @getContent="createComponent"
    ></app-form>
    <app-resume
      :blocks="blocks"
    ></app-resume>
  </div>
  <app-comments
  ></app-comments>
</template>

<script>
import AppForm from './components/AppForm'
import AppResume from './components/AppResume'
import AppComments from './components/AppComments'
export default {
  data() {
    return {
      type: 'ResumeTitle',
      content: '',
      blocks: []
    }
  },
  methods: {
    createComponent() {
      let newBlock = { id: Math.random(), type: this.type, content: this.content }
      this.blocks.push(newBlock)
      this.content = ''
      this.type = 'ResumeTitle'
    }
  },
  components: {
    AppForm,
    AppResume,
    AppComments
  }
}
</script>

<style>
  .avatar {
    display: flex;
    justify-content: center;
  }

  .avatar img {
    width: 150px;
    height: auto;
    border-radius: 50%;
  }
</style>
