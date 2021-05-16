<script>
	export let text = '';
	
	let array = [];
	
	let person = '';
	let message = '';
	
	let type = '';
	let parsed = '';
	
	$: {
		console.log('parse', text);
		const array = text.split(': ');

		if (array.length > 1) {
		
			if (array[0].indexOf('/') === 0) {
					type = 'subject';
					person = array[0].replace('/', '');
			} else if (array[0].indexOf('\\') === 0) {
					type = 'object';
					person = array[0].replace('\\', '');
			} else if (text.indexOf('?') === 0) {
					type = 'question';
					person = array[0].replace('?', '');
			} else if (text.indexOf('!') === 0) {
					type = 'alert';
					person = array[0].replace('!', '');
			} else {
					type = 'object';
					person = array[0];
			}

			parsed = array[1]; 
		} else {
			parsed = text;
		}
	}
</script>

{#if type}
	<section class={type}>
		{#if person}
			<span>{person}</span>
		{/if}
		<p class="message">{parsed}</p>
	</section>
{:else}
	<p class="message">{parsed}</p>
{/if}

<style>
	section {
		margin: 4px 0;
	}
	
	section span {
		padding: 0 2px;
		font-size: 0.8rem;
	}

	.subject {
		align-self: flex-end;
		text-align: right;
	}
	
	.object {
		align-self: flex-start;
		text-align: left;
	}
	
	.subject p, .object p {
		padding: 4px;
		border: solid 1px;
		border-radius: 6px;
	}
	
	.question, .alert {
		align-self: center;
		text-align: center;
	}
	
	.alert p {
		padding: 4px 12px;
		border: solid 1px;
		border-radius: 16px;
	}
	
	.message {
		word-break: break-word;
		white-space: pre-wrap;
		margin: 0;
		width: fit-content;
		text-align: left;
	}

</style>
