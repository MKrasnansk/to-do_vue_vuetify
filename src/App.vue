<template>
	<v-app id="inspire">
		<v-navigation-drawer v-model="drawer" app>
			<v-img
				class="pa-3 pt-5"
				src="https://picsum.photos/1920/1080?random"
				height="230"
				gradient="to top right, rgba(100,115,201,.7), rgba(25,32,72,.7)"
			>
				<v-avatar size="70" class="mb-2">
					<img
						src="https://avatars.githubusercontent.com/u/75518450?s=400&u=dbdaa09072efb51cf05f3bc2ab544dc5b9203166&v=4"
						alt="Michal Krasnansky"
					/>
				</v-avatar>
				<div class="white--text text-subtitle-1">
					Michal Krasnansky
				</div>
				<div
					class="white--text text-subtitle-2 font-weight-light"
				>
					MKrasnansk
				</div>
			</v-img>

			<v-list dense nav>
				<v-list-item
					v-for="item in items"
					:key="item.title"
					:to="item.to"
					link
				>
					<v-list-item-icon>
						<v-icon>{{ item.icon }}</v-icon>
					</v-list-item-icon>

					<v-list-item-content>
						<v-list-item-title>{{
							item.title
						}}</v-list-item-title>
					</v-list-item-content>
				</v-list-item>
			</v-list>
		</v-navigation-drawer>

		<v-app-bar
			app
			color="#6A76AB"
			dark
			prominent
			src="https://picsum.photos/1920/1080?random"
			fade-img-on-scroll
			:height="230"
		>
			<template v-slot:img="{ props }">
				<v-img
					v-bind="props"
					gradient="to top right, rgba(100,115,201,.9), rgba(25,32,72,.9)"
				></v-img>
			</template>

			<v-container class="header-container pt-3">
				<v-row>
					<v-app-bar-nav-icon
						@click="drawer = !drawer"
					></v-app-bar-nav-icon>
					<v-spacer></v-spacer>
					<search />
				</v-row>
				<v-row>
					<v-app-bar-title class="text-h4"
						>{{ $store.state.appTitle }}
					</v-app-bar-title>
				</v-row>
				<v-row>
					<live-date-time />
				</v-row>
				<v-row v-if="$route.path === '/'">
					<field-add-task />
				</v-row>
			</v-container>
		</v-app-bar>

		<v-main>
			<router-view></router-view>
			<snackbar />
		</v-main>
	</v-app>
</template>

<script>
import Snackbar from './components/Shared/Snackbar.vue'
import FieldAddTask from './components/todo/FieldAddTask.vue'
import LiveDateTime from './components/Tools/LiveDateTime.vue'
import Search from './components/Tools/Search.vue'
export default {
	components: {
		Snackbar,
		Search,
		LiveDateTime,
		FieldAddTask
	},
	data: () => ({
		drawer: null,
		items: [
			{
				title: 'To do',
				icon: 'mdi-format-list-checks',
				to: '/'
			},
			{ title: 'About', icon: 'mdi-help-box', to: '/about' }
		]
	}),
	mounted() {
		this.$store.dispatch('getTasks')
	}
}
</script>
<style lang="scss">
.header-container {
	max-width: none !important ;
}
</style>
