<template>
	<v-container>
		<v-row>
			<Photo v-for="photo in photos" :key="photo.id" :photo="photo"></Photo>
		</v-row>
	</v-container>
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
	// async mounted() {
	// 	this.photos = await this.$axios.$get('https://jsonplaceholder.typicode.com/photos?_limit=20')
	// }
	async asyncData({ $axios }) {
  		const photos = await $axios.$get('https://jsonplaceholder.typicode.com/photos?_limit=20')
  		return { photos }
	}
}
</script>