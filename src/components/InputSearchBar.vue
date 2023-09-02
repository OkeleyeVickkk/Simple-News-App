<template>
	<input type="search" name="" id="" placeholder="Search news by keywords..." class="form-control" />
</template>

<script>
export default {
	name: "SearchBar",
};
</script>

<style scoped>
.form-control {
	@apply min-h-[2.5rem] placeholder:text-sm bg-gray-50 rounded-sm border focus:outline-none px-3 max-w-xl w-full;
}
</style>
