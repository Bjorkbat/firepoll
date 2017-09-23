<template>
  <div>
    <h5>{{question.question}}</h5>
    <ul class="list-unstyled">
      <li class="h6" v-for="response in question.responses"
        v-on:click="selectAnswer(response)"
        v-bind:class="{selected: response == answer}">
        {{response}}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['question', 'readonly'],
  data: function() {
    return {
      answer: ''
    }
  },

  methods: {

    selectAnswer: function(response) {

      if (this.readonly) {
        return;
      }

      var payload = {
        question: this.question,
        answer: response
      }
      this.answer = response;
      this.$emit('selectAnswer', payload);
    }

  }
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
  background-color: #FFF2B9;
  border: 1px solid #FFFAE7;
  border-radius: 4px;
  box-shadow: 1px 1px 1px #CCC;
  padding: 10px;
}

li.selected {
  background-color: #FFE577;
}

</style>
