<template>
	<div :class="{ completed: isCompleted }" class="todo-item">
		<span v-if="entry.completed" class="radio-full">&#9673;</span>
		<span v-else class="radio">&#9711;</span>
		<span v-on:click="completeItem" class="entry-text">{{ entry.entryText }}</span>
		<span v-on:click="deleteItem" class="itembutton delete">&cross;</span>
	</div>
</template>

<script>
export default {
	name: "ListItem",
	props: {
		entry: {
			type: Object,
			required: true,
		},
		index: Number,
	},
	methods: {
		completeItem() {
			this.$emit("complete-entry", this.index)
		},
		deleteItem() {
			this.$emit("delete-entry", this.index)
		},
	},
	computed: {
		isCompleted() {
			if (this.entry.completed) {
				return "completed"
			}

			return ""
		},
	},
}
</script>

<style>
.todo-item {
	display: flex;
	align-items: center;
	margin-bottom: 12px;
	background: none;
	justify-content: space-between;
	cursor: pointer;
	color: black;
	padding: 15px 0;
	border-bottom: dashed 1px #1515e2;
}

.completed.todo-item {
	opacity: 0.7;
}

.completed.todo-item span.itembutton.complete {
	color: green;
}

span.itembutton {
	width: 10%;
	height: 20px;
	display: inline-flex;
	padding: 5px;
	align-items: center;
	border-radius: 50%;
	justify-content: center;
	transition: 0.25s;
	font-weight: bolder;
}
span.itembutton.delete:hover {
	color: #1515e2;
}

span.entry-text {
	width: 90%;
	font-size: 20px;
	text-align: left;
	font-weight: bold;
	text-transform: uppercase;
}

.completed.todo-item .entry-text {
	text-decoration: line-through;
	opacity: 0.4;
}

.radio,
.radio-full {
	display: inline-block;
	padding-right: 20px;
	color: #1515e2;
}
</style>
