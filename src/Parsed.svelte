<script>
	export let text = '';
	
	let type = '';
	let parsed = '';
	
	$: {
		if (text.indexOf('<= ') === 0) {
				type = 'subject';
				parsed = text.replace('<= ', '');
		} else if (text.indexOf('=> ') === 0) {
				type = 'object';
				parsed = text.replace('=> ', '');
		} else if (text.indexOf('== ') === 0) {
				type = 'description';
				parsed = text.replace('== ', '');
		} else if (text.indexOf('<> ') === 0) {
				type = 'alert';
				parsed = text.replace('<> ', '');
		} else {
        type = '';
				parsed = text;
		}
	}
</script>

<p class={type}>{parsed}</p>

<style>
	p {
		word-break: break-word;
	}
	
	.subject {
		text-align: right;
	}
	
	.subject::after {
		content: ' >'
	}
	
	.object {
		text-align: left;
	}
	
	.object::before {
		content: '< '
	}
	
	.description, .alert {
		text-align: center;
	}
	
	.description::before {
		content: '= ';
	}
	
	.description::after {
		content: ' =';
	}
	
	.alert::before {
		content: '<<< ';
	}
	
	.alert::after {
		content: ' >>>';
	}
</style>
