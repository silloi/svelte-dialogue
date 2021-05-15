<script>
	import TextBox from './TextBox.svelte';
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

<main class="content">
	<section class="renderer">
		{#each textList as textLine}
			<Parsed text={textLine}/>
		{/each}
	</section>

	<section class="editor">
		<TextBox bind:text={text}/>
	</section>
</main>

<style>
	.content {
		display: flex;
		flex-direction: column;
		max-width: 768px;
		height: 100vh;
	}
	
	.renderer {
		width: 100%;
		height: 50%;
		padding: 8px;
		border: solid 1px black;
		border-radius: 4px;
		box-sizing: border-box;
		overflow: auto;
	}
	
	.editor {
		width: 100%;
		height: 50%;
	}
</style>