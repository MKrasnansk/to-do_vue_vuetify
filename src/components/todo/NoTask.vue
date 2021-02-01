<template>
	<div class="no-task">
		<v-icon size="200" color="primary darken-3">
			mdi-cloud-check
		</v-icon>
		<div class="text-h3 primary--text">No Tasks</div>
	</div>
</template>

<style lang="scss" scoped>
.no-task {
	opacity: 0.5;
	display: block;
	text-align: center;
	position: absolute;
	top: 50%;
	left: 50%;
	transform: translate(-50%, -50%);
}
</style>
