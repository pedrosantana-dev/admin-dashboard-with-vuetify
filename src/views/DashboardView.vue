<template>
	<div class="dashboard">
		<v-subheader class="d-flex justify-space-between align-center">
			<h3>Dashboard</h3>
			<v-btn color="success">Ver Pedidos</v-btn>
		</v-subheader>
		<v-row>
			<v-col
				cols="12"
				lg="7"
			>
				<v-alert
					density="compact"
					type="success"
					class="my-4"
				>
					<strong>Logado com sucesso!</strong> Seja Bem-Vindo.
				</v-alert>
				<v-row>
					<v-col
						cols="12"
						lg="6"
						v-for="(item, index) in activities"
						:key="index"
					>
						<v-card
							elevation="2"
							class="rounded-lg"
						>
							<v-card-text class="d-flex justify-space-between align-center">
								<div class="">
									<strong class="d-block">{{ item.title }}</strong>
									<small>Últimas duas semanas</small>
								</div>
								<v-avatar
									:color="item.color"
									size="60"
								>
									<span>{{ item.amouts }}</span>
								</v-avatar>
							</v-card-text>
						</v-card>
					</v-col>
				</v-row>
			</v-col>

			<v-col
				cols="12"
				lg="5"
			>
				<v-card>
					<v-card-title>Atividades</v-card-title>
					<v-card-text>
						<v-timeline
							side="end"
							align="start"
						>
							<v-timeline-item
								dot-color="red"
								size="small"
							>
								<div class="d-flex">
									<div>
										<strong>50 minutos atrás</strong>
										<div class="text-caption">Mobile App</div>
									</div>
								</div>
							</v-timeline-item>

							<v-timeline-item
								dot-color="green-lighten-2"
								size="small"
							>
								<div class="d-flex">
									<div>
										<strong>10 minutos atrás</strong>
										<div class="text-caption mb-2">Hangouts</div>
									</div>
								</div>
							</v-timeline-item>

							<v-timeline-item
								dot-color="teal-lighten-3"
								size="small"
							>
								<div class="d-flex">
									<div>
										<strong>3 minutos atrás</strong>
										<div class="text-caption">Web App</div>
									</div>
								</div>
							</v-timeline-item>
						</v-timeline>
					</v-card-text>
				</v-card>
			</v-col>
		</v-row>

		<v-row>
			<v-col cols="12">
				<v-data-table-virtual
					:headers="headers"
					:items="virtualDesserts"
					class="elevation-1"
					height="400"
					item-value="name"
				>
					<template v-slot:item.action>
						<v-btn
							color="success"
							density="compact"
							>Ver</v-btn
						>
					</template>
				</v-data-table-virtual>
			</v-col>
		</v-row>
	</div>
</template>

<script>
	import { VDataTableVirtual } from 'vuetify/labs/VDataTable';
	export default {
		components: { VDataTableVirtual },
		data() {
			return {
				activities: [
					{ title: 'Total de Produtos', color: 'red', amouts: 4565 },
					{ title: 'Total de Categorias', color: 'purple', amouts: 23 },
					{ title: 'Total de Pedidos', color: 'indigo', amouts: 201 },
					{ title: 'Pedidos Pendentes', color: 'light-blue', amouts: 15 },
				],
				headers: [
					{
						title: 'Dessert (100g serving)',
						align: 'start',
						sortable: false,
						key: 'name',
					},
					{ title: 'Calories', align: 'end', key: 'calories' },
					{ title: 'Fat (g)', align: 'end', key: 'fat' },
					{ title: 'Carbs (g)', align: 'end', key: 'carbs' },
					{ title: 'Protein (g)', align: 'end', key: 'protein' },
					{ title: 'Iron (%)', align: 'end', key: 'iron' },
					{ title: 'Ação', align: 'end', key: 'action' },
				],
				desserts: [
					{
						name: 'Frozen Yogurt',
						calories: 159,
						fat: 6.0,
						carbs: 24,
						protein: 4.0,
						iron: '1',
					},
					{
						name: 'Ice cream sandwich',
						calories: 237,
						fat: 9.0,
						carbs: 37,
						protein: 4.3,
						iron: '1',
					},
					{
						name: 'Eclair',
						calories: 262,
						fat: 16.0,
						carbs: 23,
						protein: 6.0,
						iron: '7',
					},
					{
						name: 'Cupcake',
						calories: 305,
						fat: 3.7,
						carbs: 67,
						protein: 4.3,
						iron: '8',
					},
					{
						name: 'Gingerbread',
						calories: 356,
						fat: 16.0,
						carbs: 49,
						protein: 3.9,
						iron: '16',
					},
					{
						name: 'Jelly bean',
						calories: 375,
						fat: 0.0,
						carbs: 94,
						protein: 0.0,
						iron: '0',
					},
					{
						name: 'Lollipop',
						calories: 392,
						fat: 0.2,
						carbs: 98,
						protein: 0,
						iron: '2',
					},
					{
						name: 'Honeycomb',
						calories: 408,
						fat: 3.2,
						carbs: 87,
						protein: 6.5,
						iron: '45',
					},
					{
						name: 'Donut',
						calories: 452,
						fat: 25.0,
						carbs: 51,
						protein: 4.9,
						iron: '22',
					},
					{
						name: 'KitKat',
						calories: 518,
						fat: 26.0,
						carbs: 65,
						protein: 7,
						iron: '6',
					},
				],
			};
		},
		computed: {
			virtualDesserts() {
				return [...Array(10000).keys()].map((i) => {
					const dessert = { ...this.desserts[i % 10] };
					dessert.name = `${dessert.name} #${i}`;

					return dessert;
				});
			},
		},
	};
</script>

<style></style>
