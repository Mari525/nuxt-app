<template>
	<v-container>
		<v-row>
			<Card v-for="card in cardsList" :key="card.id" :card="card"></Card>
		</v-row>
	</v-container>
</template>

<script>
import Card from '@/components/Card'

export default {
	components: {
		Card
	},
	data: () => ({
		cardsList: [],
		photos: []
	}),
	async mounted() {
		this.cardsList = await this.$axios.$get("/articles.json"),
		this.photos = await this.$axios.$get('https://jsonplaceholder.typicode.com/photos?_limit=1')
	}
}

</script>