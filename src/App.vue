<template>
  <div class="container column">
    <resume-form @block-added="addBlock"></resume-form>
    <resume-view :blocks="blocks"></resume-view>
  </div>
  <div class="container">
    <app-loader v-if="loading"></app-loader>
    <resume-comments v-else :comments="comments" @load-comments="loadComments"></resume-comments>
  </div>
</template>

<script>
import ResumeForm from './ResumeForm'
import ResumeView from './ResumeView'
import ResumeComments from './ResumeComments'
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
    async loadComments() {
      this.loading = true
      const res = await fetch('https://jsonplaceholder.typicode.com/comments?_limit=42')
      this.comments = await res.json()
      this.loading = false
    },
    addBlock(block) {this.blocks.push(block)}
  },
  components: {ResumeForm, ResumeView, ResumeComments, AppLoader}
}
</script>