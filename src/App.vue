<template>
	<div class="main">
		<div class="v-main-container">
			<div class="flex search-bar justify-center items-stretch gap-2">
				<SearchBar />
				<SearchButton />
			</div>
			<div>
				<div><NewsBody :result="data" /></div>
			</div>
		</div>
	</div>
</template>

<script>
import SearchBar from "./components/InputSearchBar.vue";
import SearchButton from "./components/SearchButton.vue";
import NewsBody from "./components/NewsBody.vue";

const apiKey = `67e2b768ef734181b918ca0d862461d3`;
const api = `https://newsapi.org/v2/top-headlines?country=us&apiKey=${apiKey}`;

const runFetch = async (api) => {
	try {
		const response = await fetch(api);
		const data = await response.json();
		return data.status == "ok" && data.articles;
	} catch (err) {
		throw new Error(err);
	}
};

export default {
	name: "App",

	methods: {},
	components: { SearchBar, SearchButton, NewsBody },
	data() {
		return {
			data: [],
			error: "",
		};
	},

	mounted() {
		runFetch(api)
			.then((data) => (this.data = data))
			.catch((err) => (this.error = err));
	},
};
</script>
<style scoped>
.main {
	@apply min-h-screen;
}
.v-main-container {
	@apply max-w-3xl mx-auto md:p-4 p-2;
}
</style>
