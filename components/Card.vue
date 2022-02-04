<template>
	<v-col class="d-flex align-stretch">
		<v-card @click.prevent="openArticle(card)" width="250" class="d-flex flex-column justify-md-space-between">
			<v-card-title>
				{{ card.name }}
			</v-card-title>
			<v-card-text>
				<!-- <Photo v-for="photo in photos" :key="photo.id" :photo="photo"></Photo> -->
				<!-- <Photo :src="getSrc(card.preview_image)"></Photo> -->
				<v-img width="250" :src="getSource(card.preview_image)"></v-img>
			</v-card-text>
			<v-card-text>
				{{ card.shortDesc }}
			</v-card-text>
		</v-card>
	</v-col>
</template>

<script>
import Photo from '@/components/Photo'

export default {
	components: {
		Photo
	},
	data: () => ({
		photos: []
	}),
	// async asyncData({ $axios }) {
  	// 	const photos = await $axios.$get('https://jsonplaceholder.typicode.com/photos?_limit=20')
  	// 	return { photos }
	// },
	async mounted() {
		this.photos = await this.$axios.$get('https://jsonplaceholder.typicode.com/photos?_limit=1')
	},
	// async asyncData({$axios, params}) {
    // 	const photos = await $axios.$get('https://jsonplaceholder.typicode.com/photos/' + params.id)
	// 	return {photos}
  	// },
	props: {
		card: {
			type: Object,
			required: true
		}
	},
	methods: {
		openArticle(card) {
			this.$router.push('/news/' + card.id)
		},
		getSource(src) {
      		// return require('~/static/images/${src}.jpeg')
			return require('~/static/images/preview.jpeg')
    	}
	}
}
</script>