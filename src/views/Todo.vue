<template>
	<div class="home">
		<field-add-task />
		<list-tasks v-if="$store.state.tasks.length" />
		<no-task v-else />
	</div>
</template>

<script>
import FieldAddTask from '../components/todo/FieldAddTask.vue'
import ListTasks from '../components/todo/ListTasks.vue'
import NoTask from '../components/todo/NoTask.vue'

export default {
	components: { FieldAddTask, ListTasks, NoTask },
	name: 'Todo'
}
</script>
