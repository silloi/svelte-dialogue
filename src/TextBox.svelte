<script>
	export let text = '';
</script>

<textarea bind:value={text} />

<style>
	textarea {
		width: 100%;
		height: 100%;
		resize:none;
	}
</style>