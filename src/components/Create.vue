<template>
  <div>

    <h1>Create A Poll</h1>
    <hr />

    <form v-on:submit.prevent="createPoll">

      <section>
        <div class="form-group">
          <label class="h2">Poll Name</label>
          <p class="lead">A good poll deserves a good name.  Give it one here.</p>
          <input type="text" class="form-control underlined big" v-model="name"
            placeholder="Give your poll a fancy name or title here">
        </div>
      </section>

      <section v-if="questions.length">
        <h2>Questions (So Far)</h2>
        <question v-for="question in questions"
          v-bind:question="question"
          v-bind:readonly="true"></question>
      </section>

      <section>
        <h2>Add Some Questions</h2>
        <p class="lead">Polls need questions, obviously.</p>

        <new-question v-on:addQuestion="addQuestion"></new-question>
      </section>

      <button type="submit" class="btn btn-primary btn-lg">
        Create Poll
      </button>

    </form>

  </div>
</template>

<script>
import md5 from 'md5';
import NewQuestion from 'components/subcomponents/NewQuestion.vue';
import Question from 'components/subcomponents/Question.vue';
export default {
  name: "Create",
  components: { NewQuestion, Question },
  data: function() {
    return {
      name: '',
      questions: []
    }
  },

  methods: {

    addQuestion: function(payload) {
      this.questions.push(payload);
    },

    createPoll: function() {

      var pollID = md5(this.name + Date.now());
      firebase.database().ref('polls/' + pollID).set({
        name: this.name,
        questions: this.questions
      });

    }

  }
}
</script>
