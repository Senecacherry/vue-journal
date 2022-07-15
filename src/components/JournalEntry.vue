<template>
  <div class="container">
    <div class="card shadow-sm">
      <h4 class="card-header">{{ entry.title }}</h4>
      <div class="card-body">Post: {{ entry.post }}</div>
      <div class="card-footer">
        <Button
          @click="editEntry = !editEntry"
          class="btn btn-sm"
          text="Edit"
          type="submit"
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
        <input name="title" v-model="title" />
        <textarea v-model="updPost" name="updPost"></textarea>
        <input type="submit" value="Save Entry" class="btn btn-success"/>
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
    };
  },
  components: { Button },
  emits: ["delete-entry", "edit-entry"],
  methods: {

    onDelete(id) {
      this.$emit("delete-entry", id);
    },
    onSubmit(e) {
      e.preventDefault();

      if (!this.title) {
        alert("Please add an entry!!");
        return;
      }

      const updPost = {
        id: Math.floor(Math.random() * 1000000),
        title: this.title,
        updPost: this.post,
      };

      console.log(updPost);

      (this.title = ""), (this.post = "");

      this.$emit("edit-entry", updPost);
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