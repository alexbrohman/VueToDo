<template>
	<ToDoList msg="Your To Dos" />
</template>

<script>
import ToDoList from "./components/ToDoList.vue"

export default {
	name: "App",
	components: {
		ToDoList,
	},
}
</script>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	color: #2c3e50;
	margin-top: 60px;
}

.content-wrap {
	width: 100%;
	max-width: 500px;
	margin: 60px auto;
	padding: 0 20px;
	box-sizing: border-box;
}
</style>
