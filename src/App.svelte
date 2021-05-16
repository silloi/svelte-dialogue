<script>
	import Editor from './Editor.svelte';
	import Renderer from './Renderer.svelte';

	let text1 = `=> You say yes

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
	
	let text3 = `/孟懿子: 問孝

子: 無違

!: 樊遲御

子: 孟孫問孝於我
我對曰無違

/樊遲: 何謂也

子: 生事之以禮
死葬之以禮
祭之以禮`;

	let text = text3;

</script>

<main class="content">
	<section class="renderer">
		<Renderer text={text}/>
	</section>

	<section class="editor">
		<Editor bind:text={text}/>
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
		box-sizing: border-box;
		overflow: auto;
	}
	
	.editor {
		width: 100%;
		height: 50%;
	}
</style>
