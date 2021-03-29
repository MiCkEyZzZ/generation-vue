<template>
  <div class="container column">
    <AppForm />
    <AppView />
  </div>
  <div class="container">
    <AppLoader v-if="loading" />
    <AppComments
        :comments="comments"
        @load-comments="handleSubmitForm"
        v-else
    />
  </div>
</template>

<script>
import AppForm from './components/AppForm'
import AppView from './components/AppView'
import AppComments from './components/AppComments'
import AppLoader from './components/AppLoader'

export default {
  data() {
    return {
      comments: [],
      loading: false
    }
  },
  methods: {
    async handleSubmitForm() {
      const url = `https://jsonplaceholder.typicode.com/comments?_limit=42`
      this.loading = true
      const response = await fetch(url)
      this.comments = await response.json()
      this.loading = false
    }
  },
  components: {AppForm, AppView, AppComments, AppLoader}
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
