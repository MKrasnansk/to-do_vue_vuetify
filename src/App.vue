<template>
	<v-app id="inspire">
		<v-navigation-drawer v-model="drawer" app>
			<v-list-item>
				<v-list-item-content>
					<v-list-item-title class="title">
						To do app
					</v-list-item-title>
					<v-list-item-subtitle>
						Vuetify ToDo
					</v-list-item-subtitle>
				</v-list-item-content>
			</v-list-item>

			<v-divider></v-divider>

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
		>
			<template v-slot:img="{ props }">
				<v-img
					v-bind="props"
					gradient="to top right, rgba(100,115,201,.7), rgba(25,32,72,.7)"
				></v-img>
			</template>

			<v-container>
				<v-row>
					<v-app-bar-nav-icon
						@click="drawer = !drawer"
					></v-app-bar-nav-icon>
					<v-spacer></v-spacer>
					<search />
				</v-row>
				<v-row>
					<v-app-bar-title>Organizer</v-app-bar-title>
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
import Search from './components/Tools/Search.vue'
export default {
	components: { Snackbar, Search },
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
	})
}
</script>
