<template>
	<v-container>
		<v-row>
			<Card v-for="card in cardsList" :key="card.id" :card="card"></Card>
		</v-row>
	</v-container>
</template>

<script>
import Card from '@/components/Card'
import Photo from '@/components/Photo'

export default {
	components: {
		Card,
		Photo
	},
	data: () => ({
		cardsList: [],
		photos: []
	}),
	async asyncData({ $axios }) {
  		const cardsList = await $axios.$get('https://demo-api.vsdev.space/api/articles')
  		return { cardsList }
	}
	// async asyncData ({ $axios, params }) {
	// 	const [photosRes] = await Promise.all([ 
	// 		$axios.get('https://jsonplaceholder.typicode.com/posts/'),
	// 		$axios.get('https://jsonplaceholder.typicode.com/photos/')
	// 	])

	// 	return {
    // 		cardsList: cardsListRes.data,
    // 		photos: photosRes.data
  	// 	}
	// }
}

</script>