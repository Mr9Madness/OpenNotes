<template>
	<div class="d-flex">
		<folder />
	</div>
</template>

<script>
import Folder from "@/components/Folder";

export default {
	name: "home",
	components: {
		Folder
	}
};
</script>

<style lang="scss">
	.d-flex {
		display: flex;
	}
</style>
