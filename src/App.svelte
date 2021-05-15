<script>
	import Parsed from './Parsed.svelte';
	
	let text = `
=> You say yes
<= I say no
=> You say stop
<= and I say go go go
<> Oh no
== Hello hello
`;
	
	$: textList = text.split('\n')
</script>

<div class="editor">
	<textarea bind:value={text} />
</div>

<div class="renderer">
	{#each textList as textLine}
	<Parsed text={textLine}/>
	{/each}
</div>

<style>
	textarea {
		width: 200px;
		height: 100px;
	}

	.renderer {
		border: solid 1px black;
		border-radius: 4px;
		padding: 8px;
		width: 200px;
	}
</style>