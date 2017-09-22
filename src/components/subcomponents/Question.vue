<template>
  <div>
    <h5>{{question.question}}</h5>
    <ul class="list-unstyled" text-align="left">
      <li v-for="response in question.responses">{{response}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['question']
}
</script>

<style scoped>
div {
  border: 1px solid #CCC;
}
</style>
