<template>
<div>
	<textarea ref="editor"></textarea>
</div>
</template>

<script lang="ts">
import Vue from "vue";
import { Component, Prop, Watch } from "vue-property-decorator";
import EasyMDE, { Options } from "easymde";

@Component
export default class Editor extends Vue
{
	@Prop() file: File;
	markdownEditor: EasyMDE = {} as EasyMDE;

	mounted()
	{
		this.markdownEditor = new EasyMDE({
			element: this.$refs.editor,
			initialValue: "# Hi \n Type something here"
		} as Options);
	}
	@Watch("file")
	onFileChange(val: File, oldVal: File)
	{
		const filereader = new FileReader();
		filereader.onload = (e) => {
			if( typeof filereader.result === "string" )
			{
				this.markdownEditor.value(filereader.result as string);
			}
		};
		filereader.readAsText(val);
	}
}
</script>

<style>
  @import '~easymde/dist/easymde.min.css';
</style>
