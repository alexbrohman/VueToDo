<template>
	<form class="todo-input" @submit.prevent="onSubmit">
		<label for="todo-message"><h2>Add a ToDo</h2></label>
		<input v-model="entry" type="text" name="todo-message" placeholder="Add a todo" />
		<input class="button" type="submit" />
	</form>
</template>

<script>
export default {
	name: "ToDoForm	",
	data() {
		return {
			entry: "",
		}
	},
	methods: {
		onSubmit() {
			this.$emit("add-to-list", this.entry)
			this.entry = ""
		},
	},
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
