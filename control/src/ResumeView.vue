<template>
  <div class="card card-w70">
    <template v-if="blocks.length">
      <component v-for="block in blocks" :key="block.id" :is="'resume-' + block.type" v-bind="{value: block.value}"></component>
    </template>
    <h3 v-else>Добавьте первый блок, чтобы увидеть результат</h3>
  </div>
</template>

<script>
import ResumeAvatar from './ResumeAvatar'
import ResumeSubtitle from './ResumeSubtitle'
import ResumeText from './ResumeText'
import ResumeTitle from './ResumeTitle'

export default {
  props: ['blocks'],
  components: {ResumeTitle, ResumeText, ResumeSubtitle, ResumeAvatar
  }
}
</script>