<template>
  <div>
    <form @submit="addTodo">
			<input type="text" v-model="title" placeholder="Add Todo...">
      <input type="submit" value="Add" class="btn">
    </form>
  </div>
</template>

<script>
import uuid from 'uuid';
export default {
	name: "AddTodo",
	data() {
		return {
			title: ''
		}
	},
	methods: {
		addTodo(e) {
			// Prevent form to submit to a file
			e.preventDefault() 
			const newTodo = {
				id: uuid.v4(),
				title: this.title,
				isCompleted: false
			}
			// Send up to parent
			this.$emit('add-todo', newTodo);
			this.title = ''
		}
	}
};
</script>

<style scoped>
form {
  display: flex;
}
input[type="text"] {
  flex: 10;
  padding: 5px;
}
input[type="submit"] {
  flex: 2;
}
</style>
