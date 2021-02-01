<template>
	<v-dialog :value="true" persistent max-width="290">
		<v-card>
			<v-card-title class="headline primary--text">
				Delete!
			</v-card-title>
			<v-card-text>Určite chcte vzmazať úlohu?</v-card-text>
			<v-card-actions>
				<v-spacer></v-spacer>
				<v-btn
					@click="$emit('close')"
					color="primary lighten-3"
					text
				>
					Nie
				</v-btn>
				<v-btn
					@click="$store.dispatch('deleteTask', task.id)"
					color="red darken-9"
					text
				>
					Áno
				</v-btn>
			</v-card-actions>
		</v-card>
	</v-dialog>
</template>

<script>
export default {
	props: ['task']
}
</script>

<style lang="scss" scoped>
.headline {
	color: red;
}
</style>
