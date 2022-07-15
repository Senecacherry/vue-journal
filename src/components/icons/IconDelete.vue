<template>
    <!-- <font-awesome-icon icon="fa-solid fa-trash-can" /> -->
    <i type=" button" @click="onDelete(entry.id)" class="fa-solid fa-trash-can"></i>
</template>

<script>
import JournalEntry from '../JournalEntry.vue'
export default {
    props: {
        name: 'IconDelete',
        entry: Object
    }
}
</script>