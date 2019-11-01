<template>
	<section class="d-flex">
		<div style="flex: 1 0 15%; padding: 1rem; border-right: #ccc 1px solid;">
			<header>
				Upload files or load from something else
				<input type="file" multiple value="Upload files" ref="fileUpload" @change="addToFiles"/>
			</header>
			<div>
				<a v-for="file in files" :key="file.name" @click="selectedFile = file">
					{{file.name}}
				</a>
			</div>
		</div>
		<Editor v-bind:file="selectedFile" style="flex: 1 1 100%; padding: 1rem;"/>
	</section>
</template>

<script lang="ts">
import Vue from "vue";
import { Component, Prop } from "vue-property-decorator";
import Editor from "./Editor.vue";

@Component({
	components: {
		"Editor": Editor
	}
})
export default class Folder extends Vue
{
	files: File[] = [];
	selectedFile: File = {} as File;

	removeFromFiles(file: File)
	{
		this.files.splice(this.files.indexOf(file), 1);
	}
	addToFiles()
	{
		this.files.push(...this.$refs.fileUpload.files);
	}
}
</script>
