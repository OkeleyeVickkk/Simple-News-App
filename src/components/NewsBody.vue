<template>
	<div class="mt-10 mb-4">
		<h1 class="font-bold">Recent News</h1>
	</div>
	<section class="mt-4 flex flex-col gap-y-8">
		<div v-for="(article, index) in filteredResult" :key="index" class="grid sm:grid-cols-5 grid-cols-1 gap-4">
			<div class="image-wrapper col-span-full sm:col-span-2 rounded-md overflow-hidden flex items-center">
				<img :src="article.urlToImage" alt="" class="img-fluid" />
			</div>
			<div class="flex flex-col col-span-full gap-y-3 sm:col-span-3">
				<span class="flex items-center justify-between gap-1 flex-wrap">
					<small>Author - {{ article.author ?? "Anonymous" }}</small>
					<small class="text-xs">Date: {{ article.newDate.date }}, {{ article.newDate.time }}</small>
				</span>
				<h1 class="title text-lg font-bold">{{ article.title }}</h1>
				<span class="text-sm">{{ article?.content ?? article.description }}</span>
				<span class="flex items-center justify-between">
					<small>Source - {{ article?.source?.name ?? "Unknown" }}</small>
				</span>
			</div>
		</div>
	</section>
</template>

<!-- author, content, description  -->

<script>
function filterTheDate(newDate) {
	function getTime(time) {
		const [hour, min] = [time?.split(":")[0], time?.split(":")[1]];
		return `${hour}:${min}`;
	}
	const [date, time] = newDate.split("T");

	return { date, time: getTime(time) };
}

export default {
	name: "NewsBody",
	props: ["result"],

	data() {
		return {};
	},

	methods: {},

	computed: {
		filteredResult: function () {
			let result;
			result = this.result.filter((result) => (result.content || result.description) !== null);
			result = result.map((result) => ({ ...result, newDate: filterTheDate(result.publishedAt) }));
			return result;
		},
	},
};
</script>

<style scoped>
.img-fluid {
	@apply max-w-full w-full h-full object-cover;
}
</style>
