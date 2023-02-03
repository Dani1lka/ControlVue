<template>
  <div class="container column">
    <app-form @add="addBlock"></app-form>
    <app-view :blocks="blocks"></app-view>
  </div>
  <div class="container">
    <app-loader v-if="loading"></app-loader>
    <app-comments v-else :comments="comments" @load-comments="loadcom"></app-comments>
  </div>
</template>

<script>
import AppForm from './AppForm'
import AppView from './AppView'
import AppComments from './AppComments'
import AppLoader from './AppLoader'


export default {
  data() {
    return {
      blocks: [],
      comments: [],
      loading: false
    }
  },
  methods: {
    async loadcom() {
      this.loading = true
     
    },
    addBlock(block) {
      this.blocks.push(block)
    }
  },
  components: {AppForm, AppView, AppComments, AppLoader}
}
</script>