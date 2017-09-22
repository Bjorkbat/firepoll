<template>
  <div class="new-question">

    <div class="form-group">

      <label class="h4">Question Name</label>
      <input type="text" class="form-control underlined medium"
        placeholder="What's your favorite color?">

    </div>

    <div class="form-group">
      <label class="h5">Question Type</label>

      <div>
        <div class="form-check form-check-inline">
          <label class="form-check-label">
            <input class="form-check-input" type="radio" value="option1">
            Single Choice
          </label>
        </div>
        <div class="form-check form-check-inline">
          <label class="form-check-label">
            <input class="form-check-input" type="radio" value="option2">
            Multiple Choice
          </label>
        </div>
      </div>

    </div>

    <div class="form-group">
      <label class="h5">Responses</label>
      <new-response></new-response>
    </div>

    <button type="button" class="btn btn-default">
      Add Question
    </button>

  </div>
</template>

<script>
import NewResponse from './NewResponse.vue';
export default {
  components: { NewResponse }
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
