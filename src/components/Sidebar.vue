<template>
	<v-navigation-drawer
		permanent
		v-model="drawerIsOpen"
	>
		<v-img src="https://preview.pixlr.com/images/800wm/1439/2/1439104804.jpg">
			<div class="pa-4 text-center mt-4">
				<v-avatar
					class="mb-4"
					color="grey-darken-1"
					size="64"
				>
					<v-img
						aspect-ratio="30"
						src="https://randomuser.me/api/portraits/women/81.jpg"
					></v-img>
				</v-avatar>
				<h4 class="text-white">Admin Dashboard</h4>
			</div>
		</v-img>

		<v-divider></v-divider>

		<v-list>
			<v-list-item
				v-for="[icon, text] in links"
				:key="icon"
				:prepend-icon="icon"
				:title="text"
				link
			></v-list-item>
		</v-list>
	</v-navigation-drawer>
</template>

<script>
	export default {
		props: {
			drawer: Boolean,
		},
		data({ $props }) {
			return {
				links: [
					['mdi-chart-line', 'Dashboard'],
					['mdi-account-outline', 'Perfil'],
					['mdi-clipboard-list-outline', 'Produtos'],
					['mdi-format-list-checks', 'Pedidos'],
					['mdi-cog-outline', 'Configurações'],
				],
				drawerIsOpen: $props.drawer,
			};
		},
		watch: {
			drawer(newValue) {
				this.drawerIsOpen = newValue;
			},
		},
	};
</script>

<style></style>
