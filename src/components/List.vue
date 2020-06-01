<template>
  <div class="add-item">
    <form id="add-form">
      <h3>Add a new goal to your bucketlist</h3>
      <div class="form-group">
        <label for="goal">What are you dreaming of?</label>
        <input id="goal"
               type="text"
               v-model="goalItem">
      </div>
      <!-- <div class="form-group">
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
      </div> -->
      <button class="btn"
              @click.prevent="addGoal">Add goal</button>
    </form>

    <h2 v-if="addedGoal">My bucketlist</h2>
    <ol class="bucket-list"
        v-if="addedGoal">
      <li v-for="goal in goals" v-bind:key="goal.title">
        <list-item
          v-if="!isEdited"
          :title="goal.title"
          :content="goal.description"
          :newGoal="editedGoal"
          @editGoalText="newGoal = $event"></list-item>
        <list-item-edit
          v-if="isEdited"
          :title="goal.title"
          :content="goal.description"
          :newGoal="editedGoal"
          @editGoalText="newGoal = $event"
          @editState="edited = $event"></list-item-edit>
          <button
            v-if="!isEdited"
            class="small"
            @click="showEditForm()">Edit</button>
      </li>
    </ol>
  </div>
</template>

<script>
import ListItem from './ListItem.vue';
import ListItemEdit from './ListItemEdit.vue';

// import Done from './Done.vue';

export default {
  components: {
    ListItem,
    ListItemEdit,
    // Done,
  },
  data() {
    return {
      goalItem: '',
      descriptionText: '',
      isDone: false,
      goals: [],
      addedGoal: false,
      isEdited: false,
      editedGoal: '',
      newGoal: '',
    };
  },
  methods: {
    addGoal() {
      const titleValue = this.goalItem && this.goalItem.trim();
      const descValue = this.descriptionText && this.descriptionText.trim();
      if (!titleValue) {
        return;
      }
      this.goals.push({
        title: titleValue,
        isDone: this.isDone,
        description: descValue,
      });
      this.goalItem = '';
      this.descriptionText = '';
      this.addedGoal = true;
    },
    showEditForm() {
      this.isEdited = true;
    },
  },
};
</script>

<style scoped>
  form {
    max-width: 400px;
    padding: 15px 0;
    margin: 0 auto;
  }
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
  a {
    color: #00c690;
  }
  button {
    border: 2px solid #00c690;
    padding: 10px 20px;
    font-size: 16px;
    text-transform: uppercase;
    background-color: #fff;
    color: #00c690;
  }
  button:hover {
    color: #fff;
    background-color: #00c690;
  }
  button.small {
    padding: 2px 7px;
    font-size: 12px;
    position: absolute;
    right: 0;
    top: 15px;
    z-index: 2;
  }
  .bucket-list {
    border: 2px solid #032e3e;
    padding: 15px 30px;
    max-width: 400px;
    margin: 0 auto;
  }
  .bucket-list li {
    border-bottom: 2px solid #032e3e;
    padding: 15px;
    text-align: left;
    position: relative;
  }
  .bucket-list li:last-child {
    border-bottom-width: 0;
  }
</style>
