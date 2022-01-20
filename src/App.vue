<template>
  <div id="app">
    <v-form />
  </div>
</template>

<script>
import vForm from './components/v-form.vue'

export default {
  name: 'App',
  components: {
    vForm
  }
}
</script>

<style>
#app{
  display: flex;
  justify-content: center;
}
</style>
