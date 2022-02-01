<template>
	<v-container>
		<!-- <div class="text-h2"> {{ $card.id }} </div> -->
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
	async asyncData({$axios, params}) {
		this.cardsList = await this.$axios.$get("/articles.json/" + params.id),
		this.photos = await this.$axios.$get('https://jsonplaceholder.typicode.com/photos?_limit=1')
	}
}

</script>