<template>
	<textarea ref="editor"></textarea>
</template>

<script lang="ts">
import Vue from "vue";
import { Component, Prop } from "vue-property-decorator";
import EasyMDE, { Options } from "easymde";

@Component
export default class Editor extends Vue
{
	markdownEditor: EasyMDE = {} as EasyMDE;

	mounted()
	{
		this.markdownEditor = new EasyMDE({
			element: this.$refs.editor,
			initialValue: "# Hi \n Type something here"
		} as Options);
	}
}
</script>

<style>
  @import '~easymde/dist/easymde.min.css';
</style>
