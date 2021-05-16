<script>
	export let text = '';
	
	let array = [];
	
	let person = '';
	let message = '';
	
	let type = '';
	let parsed = '';
	
	$: {
		const array = text.split(': ');
		
		console.log('array', array);
		
		if (array.length > 1) {
		
			if (array[0].indexOf('/') === 0) {
					type = 'subject';
					person = array[0].replace('/', '');
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
		<p>{parsed}</p>
	</section>
{:else}
	<p>{parsed}</p>
{/if}

<style>
	section {
		margin: 4px 0;
	}
	
	section span {
		padding: 0 2px;
		font-size: 0.8rem;
	}
	
	section p {
		word-break: break-word;
		white-space: pre-wrap;
		border: solid 1px;
		border-radius: 6px;
		margin: 0;
		padding: 4px;
		width: fit-content;
	}

	.subject {
		align-self: flex-end;
		text-align: right;
	}
	
	.object {
		align-self: flex-start;
		text-align: left;
	}

	.question, .alert {
		align-self: center;
		text-align: center;
	}
</style>
