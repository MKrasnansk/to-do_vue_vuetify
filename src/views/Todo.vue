<template>
	<div class="home">
		<list-tasks v-if="$store.state.tasks.length" />
		<no-task v-else />
		<button-done-sorting v-if="$store.state.sorting" />
	</div>
</template>

<script>
import ButtonDoneSorting from '../components/todo/ButtonDoneSorting.vue'
import ListTasks from '../components/todo/ListTasks.vue'
import NoTask from '../components/todo/NoTask.vue'

export default {
	components: {
		ListTasks,
		NoTask,
		ButtonDoneSorting
	},
	name: 'Todo'
}
</script>
