<template>
  <div>
    <input type="text" class="form-control" v-model="response"
      placeholder="Enter response here">
    <button type="button" class="btn btn-default" v-on:click="addResponse">
      Add Another
    </button>
  </div>
</template>

<script>
export default {

  data: function() {
    return {
      response: ''
    }
  },

  methods: {
    addResponse: function() {
      this.$emit('addResponse', this.response);
      this.response = '';
    }
  }
}
</script>

<style scoped>
div {
  display: flex;
}

button {
  margin-left: 10px;
}
</style>
