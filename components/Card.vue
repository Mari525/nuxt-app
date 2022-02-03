<template>
	<v-col class="d-flex align-stretch">
		<v-card @click.prevent="openArticle(card)" width="250">
			<v-card-title>
				{{ card.title }}
			</v-card-title>
			<v-card-text>
				<Photo v-for="photo in photos" :key="photo.id" :photo="photo"></Photo>
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
		}
	}
}
</script>