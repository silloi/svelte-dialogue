<script>
	import Parsed from './Parsed.svelte';
	import Parsed2 from './Parsed2.svelte';
	
	export let text = '';
	
	$: textList = text.replace(/(\n){2,}/g, '\n\n').split('\n\n')
</script>

<div class="renderer-inner">
	{#each textList as textLine}
		<!-- <Parsed text={textLine}/> -->
		<Parsed2 text={textLine}/>
	{/each}
</div>

<style>
	.renderer-inner {
		display: flex;
		flex-direction: column;
		padding: 8px;
	}
</style>
