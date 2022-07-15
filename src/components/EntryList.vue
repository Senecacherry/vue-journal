<template>
  <div class="container">
    <AddEntry @add-entry="addEntry" />

    <h3>My Entries</h3>

    <div :key="entry.id" v-for="entry in entries">
      <JournalEntry @delete-entry="deleteEntry" @edit-entry="editEntry" :entry="entry" />
    </div>
  </div>
</template>

<script>
import JournalEntry from "./JournalEntry.vue";
import AddEntry from "./AddEntry.vue";

export default {
  name: "EntryList",
  data: function () {
    return {
      entries: Array,
    };
  },
  components: {
    JournalEntry, AddEntry
  },
  emits: ['delete-entry', 'edit-entry'],
  methods: {
    addEntry(entry) {
        this.entries = [...this.entries, entry]
    },
    deleteEntry(id) {
        if(confirm('Are you sure?')) {
        this.entries = this.entries.filter((entry) => entry.id !== id);
        }
    },
    editEntry(entry) {
        console.log('edit entry', id, editEntry);
        this.entries = [...this.entries, entry]
        // this.entries = this.entries.map((entry) => entry.id === id )
    }
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
</style>