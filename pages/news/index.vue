<template>
	<v-container>
		<v-row>
			<Card v-for="card in cardsList" :key="card.id" :card="card"></Card>
		</v-row>
	</v-container>
</template>

<script>
import Card from '@/components/Card'
// import axios from 'axios'

export default {
	components: {
		Card
	},
	data: () => ({
		cardsList: []
		// photos: []
	}),
	// async asyncData( {$axios} ) {
		// const cardsList = await this.$axios.$get('https://jsonplaceholder.typicode.com/posts')
		// return {cardsList}
		// this.photos = await this.$axios.$get('https://jsonplaceholder.typicode.com/photos?_limit=1')
	// }
	async asyncData({ $axios }) {
  		const cardsList = await $axios.$get('https://jsonplaceholder.typicode.com/posts/')
  		return { cardsList }
	}
}

</script>