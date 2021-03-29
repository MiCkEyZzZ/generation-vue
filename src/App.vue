<template>
  <div class="container column">
    <AppForm @item-added="handleCreateBlock" />
    <AppView :blocks="blocks" />
  </div>
  <div class="container">
    <AppLoader v-if="loading" />
    <AppComments
        v-else
        :comments="comments"
        @load-comments="handleSubmitForm"
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
      blocks: [],
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
    },
    handleCreateBlock(block) {
     this.blocks.push(block)
    }
  },
  components: {AppForm, AppView, AppComments, AppLoader}
}
</script>

<style>

</style>
