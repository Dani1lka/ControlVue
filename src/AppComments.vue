<template>
  <div class="card" v-if="comments.length">
    <h2>Коментарии</h2>
    <ul class="list">
      <li class="list-item" v-for="comment in comments" :key="comment.id">
        <div>
          <p><strong>{{comment.email}}</strong></p>
          <small>{{comment.body}}</small>
        </div>
      </li>
    </ul>
  </div>
  <div v-else>
    <button class="btn primary" @click="$emit('load-comments')">Загрузить коментарии</button>
    <div class="card">
      <h2>Комментарии</h2>
      <ul class="list">
        <li class="list-item">
          <div>
            <p><strong>test@microsoft.com</strong></p>
            <small>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Eligendi, reiciendis.</small>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  emits: ['load-comments'],
  props: ['comments']
}
</script>