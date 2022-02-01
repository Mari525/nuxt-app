<template>
	<v-container>
		<!-- <div class="text-h2"> {{ $card.id }} </div> -->
		<Photo v-for="photo in photos" :key="photo.id" :photo="photo"></Photo>
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
	async mounted() {
		// this.cardsList = await this.$axios.$get("/articles.json/" + params.id),
		this.photos = await this.$axios.$get('https://jsonplaceholder.typicode.com/photos?_limit=1')
	}
}

</script>