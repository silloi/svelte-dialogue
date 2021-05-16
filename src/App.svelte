<script>
	import Editor from './Editor.svelte';
	import Parsed from './Parsed.svelte';
	import Parsed2 from './Parsed2.svelte';

	let text = `=> You say yes

<= I say no

=> You say stop

<= and I say go go go

<> Oh no

== Hello hello`;

	let text2 = `You: You say yes

/I: I say no

: You say stop

/: and I say go go go

!: Oh no

?: You say good bye?

and I say Hello.`;

	$: textList = text2.split('\n\n')
</script>

<main class="content">
	<section class="renderer">
		{#each textList as textLine}
			<!-- <Parsed text={textLine}/> -->
			<Parsed2 text={textLine}/>
		{/each}
	</section>

	<section class="editor">
		<Editor bind:text={text2}/>
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
		display: flex;
		flex-direction: column;
	}
	
	.editor {
		width: 100%;
		height: 50%;
	}
</style>
