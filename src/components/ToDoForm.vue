<template>
	<div class="todo-input">
		<div class="content-wrap">
			<form autocomplete="off" @submit.prevent="onSubmit">
				<label for="todo-message"><h2>Another List App</h2></label>
				<div class="todo-input-wrapper">
					<input class="todo-message" v-model="entry" type="text" name="todo-message" />

					<input value="&plus;" class="button" type="submit" :disabled="entry.length == 0" />
				</div>
			</form>
		</div>
	</div>
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
<style scoped>
h2 {
	color: #1515e2;
	font-size: 38px;
	font-weight: bold;
	font-family: "Berkshire Swash", cursive;
	margin-bottom: 34px;
}
.todo-input-wrapper {
	display: flex;
	justify-content: space-between;
}

.todo-message {
	border: none;
	border-bottom: solid 2px;
	width: 70%;
	transition: 0.2s;
	font-size: 20px;
	text-align: left;
	font-weight: bold;
	text-transform: uppercase;
}

.todo-message:focus {
	outline: none;
}
.button {
	border: none;
	background: #e0e0ff;
	border-radius: 100px;
	color: #1515e2;
	font-size: 20px;
	font-weight: bold;
	cursor: pointer;
	transition: 0.2s;
	width: 50px;
	height: 50px;
}

.button:focus,
.button:hover,
.button:active {
	outline: none;
	background: #b5b5fb;
}

.button:disabled {
	opacity: 0.3;
}
</style>
