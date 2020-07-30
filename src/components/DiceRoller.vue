<template>
	<div>
		<v-card
			max-width="50vw"
			class="mx-auto my-10"
		>
			<v-list-item>
				<v-list-item-content>
					<v-list-item-title class="headline deep-purple--text text--accent-4-1">{{msg}}</v-list-item-title>
					<v-list-item-subtitle>Choose your weapon</v-list-item-subtitle>
				</v-list-item-content>
			</v-list-item>

			<v-img
				src="https://wallpaperaccess.com/full/1588509.jpg"
				height="180"
			></v-img>

			<v-card-text 
				align="center"
			>
				Lorem ipsum dolor sit amet, consectetur adipiscing elit.
			</v-card-text>

			<v-data-table
				:sortable="true"
				:headers="headers"
				:items="desserts"
				:items-per-page="7"
				:hide-default-footer="true"
			></v-data-table>

			<v-card-actions>
				<v-btn
					text
					color="deep-purple accent-4"
				>
					How To
				</v-btn>
				<v-spacer></v-spacer>
				<v-btn 
					icon
					color="deep-purple accent-4"
				>
					<v-icon>mdi-close</v-icon>
				</v-btn>
			</v-card-actions>
		</v-card>
  </div>
</template>

<script>
export default {
	data: () => ({
		headers: [
			{
				text: 'Die',
				align: 'start',
				sortable: false,
				value: 'die',
			},
			{ text: 'Count', value: 'count' },
			{ text: '+ -', value: 'plusminus' },
			{ text: 'Modifier', value: 'modifier' },
			{ text: 'Roll', value: 'roll' },
			{ text: 'Result', value: 'result' },
		],
		desserts: [
			{
				name: 'Frozen Yogurt',
				calories: 159,
				fat: 6.0,
				carbs: 24,
				protein: 4.0,
				iron: '1%',
			},
			{
				name: 'Ice cream sandwich',
				calories: 237,
				fat: 9.0,
				carbs: 37,
				protein: 4.3,
				iron: '1%',
			},
			{
				name: 'Eclair',
				calories: 262,
				fat: 16.0,
				carbs: 23,
				protein: 6.0,
				iron: '7%',
			},
			{
				name: 'Cupcake',
				calories: 305,
				fat: 3.7,
				carbs: 67,
				protein: 4.3,
				iron: '8%',
			},
			{
				name: 'Gingerbread',
				calories: 356,
				fat: 16.0,
				carbs: 49,
				protein: 3.9,
				iron: '16%',
			},
			{
				name: 'Jelly bean',
				calories: 375,
				fat: 0.0,
				carbs: 94,
				protein: 0.0,
				iron: '0%',
			},
			{
				name: 'Lollipop',
				calories: 392,
				fat: 0.2,
				carbs: 98,
				protein: 0,
				iron: '2%',
			},
			{
				name: 'Honeycomb',
				calories: 408,
				fat: 3.2,
				carbs: 87,
				protein: 6.5,
				iron: '45%',
			},
			{
				name: 'Donut',
				calories: 452,
				fat: 25.0,
				carbs: 51,
				protein: 4.9,
				iron: '22%',
			},
			{
				name: 'KitKat',
				calories: 518,
				fat: 26.0,
				carbs: 65,
				protein: 7,
				iron: '6%',
			},
		],
	}),
	props: {
			msg: String
	},
}
</script>

<style>

</style>