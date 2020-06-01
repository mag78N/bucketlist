<template>
  <div class="edit-item">
    <form id="edit-form">
      <div class="form-group">
        <p v-if="!editedGoal">{{ title }}</p>
        <p v-else>{{ editedGoal }}</p>
        <input id="editedGoal"
               type="text"
               v-model="editedGoal">
      </div>
      <div class="form-group">
        <label for="done">Done?
          <input id="done"
                 type="checkbox"
                 v-model="isDone">
        </label>
      </div>
      <div v-if="isDone" class="form-group">
        <label for="description">How did you fulfill your dream?</label>
        <textarea id="description"
                  rows="5"
                  v-model="editedDescription"
                  ></textarea>
      </div>
      <div class="button-container">
        <button class="small"
                @click.prevent="editGoal">Edit goal</button>
        <button class="small cancel"
                @click.prevent="cancel">Cancel</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      editedGoal: '',
      description: '',
      isDone: false,
      editFinished: false,
    };
  },
  props: ['title', 'content', 'newGoal'],
  methods: {
    editGoal() {
      this.$emit('editGoalText', this.editedGoal);
      this.editFinished = true;
      this.isEdited = false;
      this.$emit('editState', this.isEdited);
    },
    cancel() {
      this.isEdited = false;
    },
  },
  computed: {
    goalAfterEdit() {
      return this.editedGoal;
    },
  },
  directives: {
    focus: {
      inserted(el) {
        el.focus();
      },
    },
  },
};
</script>

<style scoped>

input[type="text"],
textarea {
  border: 2px solid #032e3e;
  padding: 5px;
  display: block;
  width: 100%;
  margin-top: 7px;
}
.button-container {
  margin-top: 10px;
}
button {
  border: 2px solid #00c690;
  padding: 10px 20px;
  font-size: 16px;
  text-transform: uppercase;
  background-color: #fff;
  color: #00c690;
}
button.small {
  padding: 5px 10px;
  font-size: 12px;
}
button.cancel {
  margin-left: 15px;
  border-color: #e5e5e5;
  color: #e5e5e5;
}
button:hover {
  color: #fff;
  background-color: #00c690;
}
button.cancel:hover {
  background-color: grey;
}
</style>
