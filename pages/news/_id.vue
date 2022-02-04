<template>
	<v-container class="d-flex flex-column align-center">
		<div class="text-h4 mt-10 mb-10"> {{ article.name }} </div>
		<p class="mb-10"> {{ article.date }} </p>
		<div class="d-flex">
			<v-img width="400" :src="getSource(article.full_image)" class="mr-10"></v-img>
			<v-img :src="image.url" width="300"></v-img>
		</div>
		<p class="mt-10"> {{ article.desc }} </p>
	</v-container>
</template>

<script>

export default {
	data: () => ({
		article: [],
		image: []
	}),
	// async mounted() {
	// 	this.image = await this.$axios.$get('https://jsonplaceholder.typicode.com/photos/1')
	// },
	// async asyncData({$axios, params}) {
    // 	const image = await $axios.$get('https://jsonplaceholder.typicode.com/photos/' + params.id)
	// 	return {image}
  	// },
	// async asyncData({$axios, params}) {
    // 	const article = await $axios.$get('https://jsonplaceholder.typicode.com/posts/' + params.id)
    // 	return {article}
  	// }
	async asyncData ({ $axios, params }) {
		const [articleRes, imageRes] = await Promise.all([ 
			$axios.get('https://demo-api.vsdev.space/api/articles/' + params.id),
			$axios.get('https://jsonplaceholder.typicode.com/photos/' + params.id)
		])

		return {
    		article: articleRes.data,
    		image: imageRes.data,
  		}
	},
	methods: {
		openArticle(card) {
			this.$router.push('/news/' + card.id)
		},
		getSource(src) {
      		// return require('~/static/images/${src}.jpeg')
			return require('~/static/images/full.jpeg')
    	}
	}
}

</script>