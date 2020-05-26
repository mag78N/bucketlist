<template>
  <div>
    <div class="form-group">
        <label for="done">Done already?
          <input id="done"
                 type="checkbox"
                 v-model="isDone">
        </label>
      </div>
      <div v-if="isDone" class="form-group">
        <label for="description">How did you fulfill your dream?</label>
        <textarea id="description"
                  rows="5"
                  v-model="descriptionText"
                  ></textarea>
      </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      descriptionText: '',
      isDone: false,
    };
  },
};
</script>

<style scoped>
  .form-group {
    display: block;
    margin-bottom: 15px;
  }
  input[type="text"],
  textarea {
    border: 2px solid #032e3e;
    padding: 5px;
    display: block;
    width: 100%;
    margin-top: 7px;
  }
</style>
