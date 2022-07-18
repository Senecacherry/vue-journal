<template>
  <div class="container">
    <div v-if="showAddEntry">
      <AddEntry @add-entry="addEntry" />
    </div>
    <div class="row">
      <div class="entryHeader, col">
        <h3>My Entries</h3>
      </div>
      <div class="col">
        <Button
          type="submit"
          text="Add Entry"
          color="green"
          @click="showAddEntry = 'true'"
        />
      </div>
    </div>
    <div :key="entry.id" v-for="entry in entries">
      <JournalEntry
        @delete-entry="deleteEntry"
        @edit-entry="editEntry"
        :entry="entry"
      />
    </div>
  </div>
</template>

<script>
import JournalEntry from "./JournalEntry.vue";
import AddEntry from "./AddEntry.vue";
import Button from "./Button.vue";

export default {
  name: "EntryList",
  data: function () {
    return {
      entries: Array,
      showAddEntry: false,
    };
  },
  components: {
    JournalEntry,
    AddEntry,
    Button,
  },
  emits: ["delete-entry", "edit-entry"],
  methods: {
    addEntry(entry) {
      this.entries = [...this.entries, entry];
      this.showAddEntry = false;
    },
    deleteEntry(id) {
      if (confirm("Are you sure?")) {
        this.entries = this.entries.filter((entry) => entry.id !== id);
      }
    },
    editEntry(entry) {
      console.log("edit entry", id, editEntry);
      this.entries = [...this.entries, entry];
      // this.entries = this.entries.map((entry) => entry.id === id )
    },
  },
  created() {
    this.entries = [
      {
        id: 1,
        title: "Today was a good day!",
        post: "werk werk werk",
      },
      {
        id: 2,
        title: "Activity",
        post: "Went for a jog today!",
      },
      {
        id: 3,
        title: "possible job!",
        post: "Reaching out to the universe",
      },
    ];
  },
};
</script>

<style scoped>
.container {
  max-width: 500px;
  margin: 15px auto;
  overflow: auto;
  border: 1px;
  padding: 15px;
  border-radius: 5px;
}
button {
  float: right;
}
.entryHeader {
  text-transform: uppercase;
}
</style>