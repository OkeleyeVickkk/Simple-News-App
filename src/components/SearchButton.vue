<template>
	<button
		type="button"
		class="cursor-pointer flex items-center justify-center md:py-3 p-3 text-xs bg-blue-600 rounded-sm shadow text-white hover:bg-blue-700 transition-[background_color] duration-300 ease-in-out gap-x-2">
		<span class="hidden sm:inline-block">Search</span>
		<span class="w-4 h-4">
			<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
				<path
					fill="none"
					stroke="currentColor"
					stroke-linecap="round"
					stroke-linejoin="round"
					stroke-width="1.5"
					d="m17 17l4 4M3 11a8 8 0 1 0 16 0a8 8 0 0 0-16 0Z" />
			</svg>
		</span>
	</button>
</template>

<script>
export default {
	name: "SearchButton",
};
</script>
