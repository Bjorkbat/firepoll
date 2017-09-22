<template>
  <div class="new-question">

    <div class="form-group">

      <label class="h4">Question Name</label>
      <input type="text" class="form-control underlined medium" v-model="question"
        placeholder="Ex: what's your favorite color?">

    </div>

    <div class="form-group">
      <label class="h5">Question Type</label>

      <div>
        <div class="form-check form-check-inline">
          <label class="form-check-label">
            <input class="form-check-input" type="radio" v-model="multiple" value="false">
            Single Choice
          </label>
        </div>
        <div class="form-check form-check-inline">
          <label class="form-check-label">
            <input class="form-check-input" type="radio" v-model="multiple" value="true">
            Multiple Choice
          </label>
        </div>
      </div>

    </div>

    <div class="form-group">
      <label class="h5">Responses</label>
      <ul class="list-unstyled">
        <li v-for="response in responses">{{response}}</li>
      </ul>
      <new-response v-on:addResponse="addResponse"></new-response>
    </div>

    <button type="button" class="btn btn-default" v-on:click="addQuestion">
      Add Question
    </button>

  </div>
</template>

<script>
import NewResponse from './NewResponse.vue';
export default {
  components: { NewResponse },

  data: function() {
    return {
      question: '',
      multiple: false,
      responses: []
    }
  },

  methods: {

    addQuestion: function() {
      var payload = {
        question: this.question,
        multiple: this.multiple,
        responses: this.responses
      };
      this.$emit('addQuestion', payload);

      this.question = '';
      this.responses = [];
    },

    addResponse: function(response) {
      this.responses.push(response);
    }

  }

}
</script>

<style scoped>
.new-question {
  border: 1px solid #CCC;
  border-radius: 10px;
  box-shadow: 1px 1px 1px #CCC;
  padding: 10px;
}
</style>
