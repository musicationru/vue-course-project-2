<template>
  <div class="container">
    <p>
      <button class="btn primary" @click="loadComments">Загрузить комментарии</button>
    </p>
    <div class="card" v-if="comments.length > 0">
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
    <div class="loader" v-if="isLoading"></div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
    data() {
        return {
            comments: [],
            isLoading: false
        }
    },
    methods: {
        async loadComments() {
            this.isLoading = true
            const { data } = await axios.get('https://jsonplaceholder.typicode.com/comments?_limit=42')
            this.comments = data
            this.isLoading = false
        }
    }
}
</script>

<style>

</style>