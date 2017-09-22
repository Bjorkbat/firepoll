<template>
  <div>

    <h1>Create A Poll</h1>
    <hr />

    <form>

      <section>
        <div class="form-group">
          <label class="h2">Poll Name</label>
          <p class="lead">A good poll deserves a good name.  Give it one here.</p>
          <input type="text" class="form-control underlined big"
            placeholder="Give your poll a fancy name or title here">
        </div>
      </section>

      <section>
        <h2>Add Some Questions</h2>
        <p class="lead">Polls need questions, obviously.</p>

        <new-question></new-question>
      </section>

      <button type="submit" class="btn btn-primary btn-lg">
        Create Poll
      </button>
      
    </form>

  </div>
</template>

<script>
import NewQuestion from 'components/subcomponents/NewQuestion.vue';
export default {
  name: "Create",
  components: { NewQuestion }
}
</script>
