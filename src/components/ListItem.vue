<template>
	<div class="todo-item">
		<span class="entry-text">{{ entry }}</span>

		<div class="actions">
			<span class="itembutton complete">&check;</span>
			<span class="itembutton delete">&cross;</span>
		</div>
	</div>
</template>

<script>
export default {
	name: "ListItem",
	props: {
		entry: {
			type: String,
			required: true,
		},
	},
	methods: {
		completeItem() {
			this.$emit("complete-entry")
		},
		deleteItem() {
			this.$emit("delete-entry")
		},
	},
}
</script>

<style>
.todo-item {
	display: flex;
	align-items: center;
	margin-bottom: 12px;
	padding: 7px;
	border: solid 1px #e2e2e2;
	background: NONE;
	justify-content: space-between;
}

span.itembutton {
	width: 20px;
	height: 20px;
	background: rgb(226, 226, 226);
	display: inline-flex;
	margin: 0 5px;
	padding: 5px;
	align-items: center;
	border-radius: 50%;
	justify-content: center;
	transition: 0.25s;
	cursor: pointer;
	font-weight: bolder;
}

span.itembutton.complete:hover {
	background: #2ca847;
	color: white;
}

span.itembutton.delete:hover {
	background: #db3705;
	color: white;
}

span.entry-text {
	width: 80%;
	text-align: left;
}
</style>
