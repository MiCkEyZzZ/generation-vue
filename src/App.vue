<template>
  <div class="container column">
    <app-form></app-form>
    <app-view></app-view>
  </div>
  <div class="container">
    <p>
      <button
          class="btn primary"
      >Загрузить комментарии</button>
    </p>
    <app-comments></app-comments>
    <app-loader></app-loader>
  </div>
</template>

<script>
import AppForm from './components/AppForm'
import AppView from './components/AppView'
import AppComments from './components/AppComments'
import AppLoader from './components/AppLoader'

export default {
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
