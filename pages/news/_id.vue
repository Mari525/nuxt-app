<template>
	<v-container class="d-flex flex-column align-center">
		<div class="text-h4 mt-10 mb-10"> {{ article.title }} </div>
		<!-- <div class="text-h2">{{ $route.params.id }}</div> -->
		<!-- <Photo v-for="photo in photos" :key="photo.id" :photo="photo"></Photo> -->
		<v-img :src="image.url" width="300"></v-img>
		<p class="mt-10"> {{ article.body }} </p>
	</v-container>
</template>

<script>
import Photo from '@/components/Photo'

export default {
	components: {
		Photo
	},
	data: () => ({
		article: [],
		// photos: [],
		image: []
	}),
	async mounted() {
		this.image = await this.$axios.$get('https://jsonplaceholder.typicode.com/photos/1')
	},
	// async asyncData({ $axios, params }) {
		// const article = await $axios.$get('https://jsonplaceholder.typicode.com/posts/' + params.id)
		// return {article}
		// this.photos = await this.$axios.$get('https://jsonplaceholder.typicode.com/photos?_limit=1')
	// }
	async asyncData({$axios, params}) {
		// const photos = await $axios.$get('https://jsonplaceholder.typicode.com/photos?_limit=1')
    	const article = await $axios.$get('https://jsonplaceholder.typicode.com/posts/' + params.id)
    	return {article}
  	},
	// async asyncData({$axios, params}) {
    // 	const photos = await $axios.$get('https://jsonplaceholder.typicode.com/photos?_limit=1')
    // 	return {photos}
  	// }
	// computed: {
	// 	image() {
	// 		const image = await $axios.$get('https://jsonplaceholder.typicode.com/photos/' + params.id)
	// 	}
	// }
}

</script>