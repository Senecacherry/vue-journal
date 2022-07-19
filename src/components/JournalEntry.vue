<template>
  <div class="container">
    <div class="card shadow-sm">
      <h4 class="card-header">{{ entry.title }}</h4>
      <div class="card-body">Post: {{ entry.post }}</div>
      <div class="card-footer">
        <Button
          @edit-entry="editEntry"
          class="btn btn-sm"
          text="Edit"
          color="grey"
        />
        <Button
          @click="onDelete(entry.id)"
          class="btn btn-sm"
          text="Delete"
          color="red"
        />
      </div>
        <div v-if="editEntry">
        <input name="title" v-model="entry.title" />
        <textarea v-model="updEntry" name="updEntry"></textarea>
        <Button text="Update Entry" @update-entry="updateEntry"></Button>
      </div>
    </div>
  </div>
</template>

<script>
import Button from "./Button.vue";
export default {
  name: "JournalEntry",
  props: {
    entry: Object,
  },
  data() {
    return {
      updPost: "",
      title: "",
      editEntry: false
    };
  },
  components: { Button },
  emits: ["delete-entry", "edit-entry", "update-entry"],
  methods: {
    toggleEditEntry() {
        console.log('hit toggle');
        this.editEntry = true;
    },
    onDelete(id) {
      this.$emit("delete-entry", id);
    },
    editEntry(id) {
        console.log('hit edit');
    //   e.preventDefault();

      if (!this.title) {
        alert("Please add an entry!!");
        return;
      }

      const editPost = {
        id: this.entry.id,
        title: this.title,
        editPost: this.post,
      };

      console.log(editPost);

      (this.title = ""), (this.post = "");

      this.$emit("create-entry", createPost);
    },
    
  },
};
</script>

<style scoped>
.card-footer,
.card-header {
  background-color: rgba(154, 217, 219, 0.161);
}
.btn {
  float: right;
  max-width: fit-content;
}
</style>