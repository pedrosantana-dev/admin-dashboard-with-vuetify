<template>
	<v-app-bar elevation="4">
		<v-app-bar-nav-icon @click="$emit('handleDrawer')"></v-app-bar-nav-icon>
		<v-spacer></v-spacer>
		<v-col cols="6">
			<v-form class="mt-5">
				<v-text-field
					rounded
					density="compact"
					variant="outlined"
					placeholder="Buscar aqui"
					append-inner-icon="mdi-magnify"
				></v-text-field>
			</v-form>
		</v-col>

		<v-spacer></v-spacer>

		<v-menu>
			<template v-slot:activator="{ props }">
				<span
					v-bind="props"
					style="cursor: pointer"
					class="mx-5"
				>
					<v-badge
						offset-x="5"
						offset-y="5"
						color="red"
						content="5"
					>
						<v-icon size="x-large">mdi-bell-outline</v-icon>
					</v-badge>
				</span>
			</template>
			<v-list
				:items="items"
				item-props
				lines="three"
			>
				<template v-slot:subtitle="{ subtitle }">
					<div v-html="subtitle"></div>
				</template>
			</v-list>
		</v-menu>

		<v-menu>
			<template v-slot:activator="{ props }">
				<span
					v-bind="props"
					style="cursor: pointer"
					class="mr-10 hidden-xs"
				>
					<v-chip link>
						<v-badge
							dot
							color="green"
						>
							<v-avatar image="https://randomuser.me/api/portraits/women/81.jpg"> </v-avatar>
						</v-badge>
						<span>Sharli Chin</span>
					</v-chip>
				</span>
			</template>
			<v-list
				width="250"
				class="py-0"
			>
				<v-list-item prepend-avatar="https://randomuser.me/api/portraits/women/81.jpg">
					<v-list-item-title> Sharli Chin </v-list-item-title>
					<v-list-item-subtitle>Logged in</v-list-item-subtitle>
				</v-list-item>
				<v-divider></v-divider>
				<v-list-item
					v-for="(item, index) in menu"
					:key="index"
					link
				>
					<template v-slot:prepend>
						<v-icon>{{ item.icon }}</v-icon>
					</template>
					<v-list-title>{{ item.title }}</v-list-title>
				</v-list-item>
			</v-list>
		</v-menu>
	</v-app-bar>
</template>

<script>
	export default {
		data() {
			return {
				menu: [
					{ title: 'Perfil', icon: 'mdi-account' },
					{ title: 'Alterar Senha', icon: 'mdi-key' },
					{ title: 'Configurações', icon: 'mdi-cog' },
					{ title: 'Sair', icon: 'mdi-logout' },
				],
				items: [
					{ type: 'subheader', title: 'Today' },
					{
						prependAvatar: 'https://cdn.vuetifyjs.com/images/lists/1.jpg',
						title: 'Brunch this weekend?',
						subtitle: `<span class="text-primary">Ali Connors</span> &mdash; I'll be in your neighborhood doing errands this weekend. Do you want to hang out?`,
					},
					{ type: 'divider', inset: true },
					{
						prependAvatar: 'https://cdn.vuetifyjs.com/images/lists/2.jpg',
						title: 'Summer BBQ',
						subtitle: `<span class="text-primary">to Alex, Scott, Jennifer</span> &mdash; Wish I could come, but I'm out of town this weekend.`,
					},
					{ type: 'divider', inset: true },
					{
						prependAvatar: 'https://cdn.vuetifyjs.com/images/lists/3.jpg',
						title: 'Oui oui',
						subtitle:
							'<span class="text-primary">Sandra Adams</span> &mdash; Do you have Paris recommendations? Have you ever been?',
					},
					{ type: 'divider', inset: true },
					{
						prependAvatar: 'https://cdn.vuetifyjs.com/images/lists/4.jpg',
						title: 'Birthday gift',
						subtitle:
							'<span class="text-primary">Trevor Hansen</span> &mdash; Have any ideas about what we should get Heidi for her birthday?',
					},
					{ type: 'divider', inset: true },
					{
						prependAvatar: 'https://cdn.vuetifyjs.com/images/lists/5.jpg',
						title: 'Recipe to try',
						subtitle:
							'<span class="text-primary">Britta Holt</span> &mdash; We should eat this: Grate, Squash, Corn, and tomatillo Tacos.',
					},
				],
			};
		},
	};
</script>

<style></style>
