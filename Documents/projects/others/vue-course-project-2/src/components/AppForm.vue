<template>
  <form class="card card-w30">
      <div class="form-control">
        <label for="type">Тип блока</label>
        <select id="type" 
          :value="type"
          @change="changeType"
          >
          <option value="ResumeTitle">Заголовок</option>
          <option value="ResumeSubtitle">Подзаголовок</option>
          <option value="ResumeAvatar">Аватар</option>
          <option value="ResumeText">Текст</option>
        </select>
      </div>

      <div class="form-control">
        <label for="value">Значение</label>
        <textarea 
          id="value" 
          rows="3" 
          :value="content"
          @input="changeContent"
          ></textarea>
      </div>

      <button :disabled="validContent" class="btn primary" @click.prevent="addContent">Добавить</button>
    </form>
</template>

<script>
export default {
  emits: ['update:type', 'update:content', 'getContent'],
  props: ['type', 'content'],
  methods: {
    addContent() {
      this.$emit('getContent')
    },
    changeType() {
      this.$emit('update:type', event.target.value)
    },
    changeContent() {
      this.$emit('update:content', event.target.value)
    }
  },
  computed: {
    validContent() {
      if (this.content.length < 4) {
        return true
      } else {
        return false
      }
    }
  }
}
</script>

<style>

</style>