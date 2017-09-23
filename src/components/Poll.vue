<template>
  <div>
    <h1>{{name}}</h1>

    <section>
      <question v-for="question in questions"
        v-bind:question="question"
        v-on:selectAnswer="selectAnswer"></question>
    </section>

    <button class="btn btn-primary btn-lg" v-on:click="sendAnswers">
      Send Answers
    </button>

  </div>
</template>

<script>
import md5 from 'md5';
import Question from 'components/subcomponents/Question.vue';
export default {

  components: { Question },

  data: function() {
    return {
      name: '',
      questions: [],
      answers: []
    }
  },

  methods: {

    selectAnswer: function(payload) {

      var multipleChoice = this.answers[j].questionIndex == i &&
        this.answers[j].answer == payload.answer;
      var singleChoice = this.answers[j].questionIndex == i &&
        !payload.question.multiple;

      // Figure out the index of the question first
      for(var i = 0; i < this.questions.length; i ++) {

        if(this.questions[i] == payload.question) {

          // If it's single-choice, then make sure that we change the original
          // answer to the new one.  Otherwise, just make sure we don't have
          // duplicate answers
          for(var j = 0; j < this.answers.length; j ++) {

            if (multipleChoice || singleChoice) {
              this.answers.splice(j, 1);
              break;
            }

          }

          this.answers.push({
            questionIndex: i,
            answer: payload.answer
          });
          break;

        }

      }

    },

    sendAnswers: function(payload) {

      var _this = this;
      var answerID = md5(Date.now());
      firebase.database().ref('answers/' + this.$route.params.id + '/' + answerID).set({
        answers: this.answers
      });

    }

  },

  mounted: function() {

    var _this = this;
    firebase.database().ref('polls/' + this.$route.params.id).once('value').then(function(snapshot) {

      _this.name = snapshot.val().name;
      _this.questions = snapshot.val().questions;

    });

  }

}
</script>
