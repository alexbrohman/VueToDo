<template>
	<ToDoForm @add-to-list="addToList" msg="Your To Dos" />
	<div class="hello">
		<h1>{{ msg }}</h1>
	</div>
	<div class="todo-list-wrap">
		<ul class="todo-list">
			<ListItem
				v-for="(entry, index) in entries"
				:key="index"
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
			entries: [],
		}
	},
	methods: {
		addToList(entry) {
			this.entries.push(entry)
		},
		completeEntry(index) {
			console.log(`Completing ${index}`)
		},
		deleteEntry(index) {
			console.log(`Deleting ${index}`)
		},
	},
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
	margin: 40px 0 0;
}
ul {
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
</style>
