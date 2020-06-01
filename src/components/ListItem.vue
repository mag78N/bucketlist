<template>
  <div class="goal-container">
    <div class="goal-title">{{ goalTitle }}</div>
    <div class="goal-content">{{ goalContent }}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isEdited: false,
      goalTitle: this.title,
      goalContent: this.content,
    };
  },
  props: ['title', 'content', 'newGoal'],
  methods: {
    showEditForm() {
      this.isEdited = true;
    },
  },
};
</script>

<style scoped>
  .goal-container {
    position: relative;
  }
  .goal-title {
    font-weight: bold;
    padding-right: 55px;
  }
  .goal-content {
    font-size: 12px;
    padding-top: 5px;
  }
</style>
