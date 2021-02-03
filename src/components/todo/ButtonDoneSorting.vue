<template>
	<v-btn
		@click="$store.commit('toggleSorting')"
		class="btn-done-sort"
		color="primary"
	>
		Done sorting
	</v-btn>
</template>

<script>
export default {}
</script>

<style lang="scss">
.btn-done-sort {
	position: fixed;
	bottom: 20px;
	left: 50%;
	transform: translate(-50%);
}
</style>
