<template>
	<ToDoForm @add-to-list="addToList" msg="Your To Dos" />

	<div class="content-wrap">
		<ul class="todo-list">
			<ListItem
				v-for="(entry, index) in entries"
				:key="index"
				:index="index"
				:entry="entry"
				@complete-entry="completeEntry"
				@delete-entry="deleteEntry"
			/>
		</ul>
	</div>
</template>

<script>
import ListItem from "./ListItem"
import ToDoForm from "./ToDoForm"

export default {
	name: "ToDoList",
	components: {
		ToDoForm,
		ListItem,
	},
	props: {
		msg: String,
	},
	data() {
		return {
			entries: localStorage.entries ? JSON.parse(localStorage.entries) : [],
		}
	},
	mounted() {
		if (localStorage.entries) {
			this.entries = JSON.parse(localStorage.entries)
		}
	},
	methods: {
		updateLocalStorage() {
			localStorage.setItem("entries", JSON.stringify(this.entries))
		},
		addToList(entry) {
			if (entry) {
				this.entries.push({
					entryText: entry,
					completed: false,
				})
				this.updateLocalStorage()
			}
		},
		completeEntry(index) {
			if (!this.entries[index]) {
				return
			}

			this.entries[index].completed = !this.entries[index].completed
			this.updateLocalStorage()
		},
		deleteEntry(index) {
			this.entries.splice(index, 1)
			this.updateLocalStorage()
		},
	},
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style>
@import url("https://fonts.googleapis.com/css2?family=Berkshire+Swash&display=swap");
</style>

<style scoped>
h3 {
	margin: 40px 0 0;
}
√ ul {
	list-style-type: none;
	padding: 0;
}
li {
	display: inline-block;
	margin: 0 10px;
}
a {
	color: #42b983;
}

.todo-list {
	padding: 0;
}
</style>
