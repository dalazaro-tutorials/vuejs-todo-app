<!-- CreateTodo component: add a new todo to the hard-coded data array using form -->
<template>
  <div class="ui basic content center aligned segment">

    <!-- if not currently creating, a button with a plus icon is rendered below the todos -->
    <button class="ui basic button icon" v-on:click="openForm" v-show="!isCreating">
      <i class="plus icon"></i>
    </button>

    <!-- if currently creating, show a form to create new todo -->
    <div class="ui centered card" v-show="isCreating">
      <div class="content">
        <h4>New To-Do</h4>

        <div class="ui form">
          <div class="field">
            <label>Title</label>
            <input v-model="titleText" type="text">
          </div>
          <div class="field">
            <label>Description</label>
            <input v-model="descriptionText" type="text">
          </div>

          <div class="ui two button attached buttons">
            <button
              class="ui basic blue button"
              v-on:click="sendForm()">
              Create
            </button>
            <button
              class="ui basic red button"
              v-on:click="closeForm">
              Cancel
            </button>
          </div>
        </div>

      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    // resets to an empty form, not currently creating
    return {
      titleText: '',
      descriptionText: '',
      isCreating: false,
    };
  },
  methods: {
    openForm() {
      this.isCreating = true;
    },
    closeForm() {
      this.isCreating = false;
    },
    sendForm() {
      if (this.titleText.length > 0 && this.descriptionText.length > 0) {
        const title = this.titleText;
        const description = this.descriptionText;
        this.$emit('create-todo', {
          title,
          description,
          done: false,
        });
        this.titleText = '';
        this.descriptionText = '';
        this.isCreating = false;
      }
    },
  },
};
</script>
