<template>
	<v-text-field
		v-model="search"
		@focus="searchClosed = false"
		@blur="searchClosed = true"
		class="expanding-search mt-1"
		:class="{ closed: searchClosed && !search }"
		placeholder="Vyhladať úlohu?"
		prepend-inner-icon="mdi-magnify"
		filled
		dense
		clearable
	></v-text-field>
</template>

<script>
export default {
	data() {
		return {
			search: null,
			searchClosed: true
		}
	}
}
</script>

<style lang="scss">
.expanding-search {
	transition: max-width 0.3s ease;
	.v-input__slot {
		cursor: pointer !important;
		&:before,
		&:after {
			border-color: transparent !important;
		}
	}
	&.closed {
		max-width: 45px;
		.v-input__slot {
			background: transparent !important;
		}
	}
}
</style>
