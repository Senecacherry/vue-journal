<template>
<div class="mb-3, addEntry">
    <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label class="form-label">Title</label>
      <input class="form-control"
        type="text"
        v-model="title"
        name="title"
        placeholder="Add a title"
      />
    </div>
    <div class="form-control">
      <label class="form-label">Post:</label>
      <textarea class="form-control" type="text" v-model="post" name="post" rows="3"></textarea>
    </div>

    <input type="submit" value="Save Entry" class="btn btn-success" />
    <!-- <Button text="Save" color="green" @add-entry="$emit('add-entry')"></Button> -->
    <Button text="Cancel" color="grey" @show-add-entry="$emit('show-add-entry')"></Button>
  </form>  
  </div>
</template>

<script>
import Button from './Button.vue';
export default {
  components: { Button },
    name: 'AddEntry',
    data() {
        return {
            title: '',
            post: ''
        }
    },
    methods: {
        onSubmit(e) {
            e.preventDefault()

            if(!this.title) {
                alert('Please add an entry!!');
                return
            }

            const newEntry = {
                id: Math.floor(Math.random() * 1000000),
                title: this.title,
                post: this.post
            }
            console.log('hit this')

            this.$emit('add-entry', newEntry)

            this.title = '',
            this.post = ''
        },
    }
}
</script>

<style scoped>
.addEntry {
    padding-bottom: 60px;
}
.add-form {
  margin-bottom: 40px;
}

.btn {
    float: right;
    margin: 10px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
}
.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}
.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>