<script lang="ts">
	let links = [
		{
			id: '1',
			url: 'https://facebook.com/'
		},
		{
			id: '2',
			url: 'https://instagram.com/'
		}
	];

	let link = '';

	$: console.log(links);
	$: if (link.includes('google')) {
		console.log('Google link');
	}

	function handleSubmit() {
		links = [...links, { id: String(links.length + 1), url: link }];

		console.log(link);
	}
</script>

<div class="p-4 space-y-4">
	<h1>Welcome to Shortus</h1>
	<div class="flex flex-col gap-2">
		{#each links as link (link.id)}
			<div class="border-slate-200 border rounded-md py-2 px-4">{link.url}</div>
		{/each}
	</div>
	<input class="w-full" bind:value={link} type="text" />
	<button on:click={handleSubmit}>Add</button>
</div>
