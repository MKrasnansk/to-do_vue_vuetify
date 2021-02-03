<template>
	<div>
		<v-menu bottom left>
			<template v-slot:activator="{ on, attrs }">
				<v-btn
					color="primary"
					icon
					v-bind="attrs"
					v-on="on"
				>
					<v-icon>mdi-dots-vertical</v-icon>
				</v-btn>
			</template>

			<v-list>
				<v-list-item
					v-for="(item, index) in items"
					:key="index"
					@click="handleClick(index)"
				>
					<v-list-item-icon>
						<v-icon v-text="item.icon"></v-icon>
					</v-list-item-icon>
					<v-list-item-title>{{
						item.title
					}}</v-list-item-title>
				</v-list-item>
			</v-list>
		</v-menu>
		<dialog-edit
			v-if="dialogs.edit"
			@close="dialogs.edit = false"
			:task="task"
		/>
		<dialog-due-date
			v-if="dialogs.dueDate"
			@close="dialogs.dueDate = false"
			:task="task"
		/>
		<dialog-delete
			v-if="dialogs.delete"
			@close="dialogs.delete = false"
			:task="task"
		/>
	</div>
</template>

<script>
import DialogEdit from './Dialogs/DialogEdit.vue'
import DialogDelete from './Dialogs/DialogDelete.vue'
import DialogDueDate from './Dialogs/DialogDueDate.vue'
export default {
	components: {
		DialogDelete,
		DialogEdit,
		DialogDueDate
	},
	props: ['task'],
	data: () => ({
		dialogs: {
			edit: false,
			dueDate: false,
			delete: false
		},
		items: [
			{
				title: 'Upraviť',
				icon: 'mdi-pencil',
				click() {
					this.dialogs.edit = true
				}
			},
			{
				title: 'Dátum',
				icon: 'mdi-timer-outline',
				click() {
					this.dialogs.dueDate = true
				}
			},
			{
				title: 'Zmazať',
				icon: 'mdi-delete-variant',
				click() {
					this.dialogs.delete = true
				}
			},
			{
				title: 'Presunúť',
				icon: 'mdi-drag-horizontal-variant',
				click() {
					if (!this.$store.state.search) {
						this.$store.commit('toggleSorting')
					} else {
						this.$store.commit(
							'showSnackbar',
							'Ukončite vzhladavanie!'
						)
					}
				}
			}
		]
	}),
	methods: {
		handleClick(index) {
			this.items[index].click.call(this)
		}
	}
}
</script>
