<template>
	<v-snackbar
		v-model="$store.state.snackbar.show"
		:timeout="timeout"
	>
		{{ $store.state.snackbar.text }}

		<template v-slot:action="{ attrs }">
			<v-btn
				@click="$store.commit('hideSnackbar')"
				text
				v-bind="attrs"
				class="snack-btn"
			>
				Close
			</v-btn>
		</template>
	</v-snackbar>
</template>

<script>
export default {
	data: () => ({
		snackbar: false,
		text: 'Task added!',
		timeout: 2000
	})
}
</script>

<style lang="scss">
div.v-snack:not(.v-snack--absolute) {
	height: 100%;
}
.snack-btn {
	background: none;
	&:hover {
		color: red;
		transition: 0.2s ease;
	}
}
</style>
