<template>
	<div>
		<v-card
			max-width="50vw"
			class="mx-auto my-10"
		>
			<v-list-item>
				<v-list-item-content>
					<v-list-item-title class="headline blue-grey--text text--accent-4-1">{{msg}}</v-list-item-title>
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
				:items="dies"
				:items-per-page="7"
				:hide-default-footer="true"
			>
				<template v-slot:item.count="props">
					<v-edit-dialog
						:return-value.sync="props.item.count"
						@save="save"
						@cancel="cancel"
						@open="open"
						@close="close"
					> {{ props.item.count }}
						<template v-slot:input>
							<v-text-field
								:maxlength="max"
								v-model="props.item.count"
								label="Edit"
								single-line
								autofocus
							></v-text-field>
						</template>
					</v-edit-dialog>
				</template>

				<template v-slot:item.mod="props">
					<v-edit-dialog
						:return-value.sync="props.item.mod"
						@save="save"
						@cancel="cancel"
						@open="open"
						@close="close"
					> {{ props.item.mod }}
						<template v-slot:input>
							<v-text-field
								:maxlength="max"
								v-model="props.item.mod"
								label="Edit"
								single-line
								autofocus
							></v-text-field>
						</template>
					</v-edit-dialog>
				</template>
				
				<template v-slot:item.plusminus="{ item }">
					<v-radio-group v-model="item.plusminus" :mandatory="true" row>
						<v-radio color="blue" label="+" value="radio-1"></v-radio>
						<v-radio color="red" label="-" value="radio-2"></v-radio>
					</v-radio-group>
        </template>

				<template v-slot:item.roll="{ item }">
					<v-btn small dark color="blue-grey darken-3" v-model="item.roll" @click="roll(item.die, item.mod)">Roll</v-btn>
        </template>

			</v-data-table>
      <v-snackbar v-model="snack" :timeout="3000" :color="snackColor">
        {{ snackText }}
        <template v-slot:action="{ attrs }">
          <v-btn v-bind="attrs" text @click="snack = false">Close</v-btn>
        </template>
      </v-snackbar>
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
		snack: false,
		snackColor: '',
		snackText: '',
		max: 3,
		dieResult: null,
		headers: [
			{ text: 'Die', align: 'start', sortable: false, value: 'die',},
			{ text: 'Count', sortable: false, value: 'count' },
			{ text: '+ -', sortable: false, value: 'plusminus' },
			{ text: 'Modifier', sortable: false, value: 'mod' },
			{ text: 'Roll', sortable: false, value: 'roll' },
			{ text: 'Result', sortable: false, value: 'result' },
		],
		dies: [
			{
				die: 'd4',
				count: 1,
				mod: Number(0),
				protein: 4.0,
				result: 0,
			},
			{
				die: 'd6',
				count: 1,
				mod: 0,
				protein: 4.3,
				result: 0,
			},
			{
				die: 'd8',
				count: 1,
				mod: 0,
				protein: 6.0,                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     
				result: 0,
			},
			{
				die: 'd10',
				count: 1,
				mod: 0,
				protein: 4.3,
				result: 0,
			},
			{
				die: 'd12',
				count: 1,
				mod: 0,
				protein: 3.9,
				result: 0,
			},
			{
				die: 'd20',
				count: 1,
				mod: 0,
				protein: 0,
				result: 0,
			},
			{
				die: 'd100',
				count: 1,
				mod: 0,
				protein: 0,
				result: 0,
			},
		],
	}),
	props: {
			msg: String
	},
	methods: {
		save () {
			this.snack = true
			this.snackColor = 'success'
			this.snackText = 'Ready to roll'
		},
		cancel () {
			this.snack = true
			this.snackColor = 'error'
			this.snackText = 'Choose how many dice to roll'
		},
		open () {
			this.snack = true
			this.snackColor = 'info'
			this.snackText = 'Choose how many dice to roll'
		},
		close () {
			console.log('Dialog closed')
		},
		roll (die, mod) {
			mod = parseInt(mod)
			switch (die) {
			case 'd4':
				this.dies[0].result = Math.floor(Math.random() * (5 - 1)) + 1 + mod
				console.log(this.dies[0].result)
				break;
			case 'd6':
				this.dies[1].result = Math.floor(Math.random() * (7 - 1)) + 1 + mod
				console.log(this.dies[1].result);
				break;
			case 'd8':
				this.dies[2].result = Math.floor(Math.random() * (9 - 1)) + 1 + mod
				console.log(this.dies[2].result);
				break;
			case 'd10':
				this.dies[3].result = Math.floor(Math.random() * (11 - 1)) + 1 + mod
				console.log(this.dies[3].result);
				break;
			case 'd12':
				this.dies[4].result = Math.floor(Math.random() * (13 - 1)) + 1 + mod
				console.log(this.dies[4].result);
				break;
			case 'd20':
				this.dies[5].result = Math.floor(Math.random() * (21 - 1)) + 1 + mod
				console.log(this.dies[5].result);
				break;
			case 'd100':
				this.dies[6].result = Math.floor(Math.random() * (101 - 1)) + 1 + mod
				console.log(this.dies[6].result);
				break;
			default:
				console.log(`Sorry, we are out of ${die}.`);
		}
		}
	}
}
</script>

<style>
	.dialog-width {
		max-width: 50px !important;
	}
</style>