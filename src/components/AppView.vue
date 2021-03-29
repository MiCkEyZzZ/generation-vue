<template>
  <div class="card card-w70">
    <template v-if="blocks.length">
      <component
          v-for="block in blocks"
          :key="block.id"
          :is="'app-' + block.type"
          v-bind="{value: block.value}"
      ></component>
    </template>
    <h3 v-else>Добавьте первый блок, чтобы увидеть результат</h3>
  </div>
</template>

<script>
import AppTitle from './UI/AppTitle'
import AppSubtitle from './UI/AppSubtitle'
import AppAvatar from './UI/AppAvatar'
import AppText from './UI/AppText'

export default {
  props: ['blocks'],
  components: {AppTitle, AppSubtitle, AppAvatar, AppText}
}
</script>

<style scoped>

</style>