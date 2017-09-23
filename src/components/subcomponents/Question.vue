<template>
  <div>
    <h5>{{question.question}}</h5>
    <ul class="list-unstyled">
      <li v-for="response in question.responses" class="h6">{{response}}</li>
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
  background-color: #FFDC45;
  border: 1px solid #FFD000;
  border-radius: 10px;
  box-shadow: 1px 1px 1px #CCC;
  margin: 10px auto;
  padding: 10px;
}

ul {
  text-align: left;
}

li {
  background-color: #FFE577;
  border: 1px solid #FFFAE7;
  border-radius: 4px;
  box-shadow: 1px 1px 1px #CCC;
  padding: 10px;
}

</style>
