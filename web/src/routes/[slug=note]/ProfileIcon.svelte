<script lang="ts">
	import { onImageError } from '$lib/Constants';
	import type { Metadata } from '$lib/Items';
	import { nip19 } from 'nostr-tools';

	export let metadata: Metadata;

	$: name = metadata.content?.display_name ?? '@' + metadata.content?.name;
</script>

<article>
	<a href="/{nip19.npubEncode(metadata.event.pubkey)}">
		<img
			src={metadata.picture}
			alt={name}
			title={name}
			on:error={onImageError}
		/>
	</a>
</article>

<style>
	a {
		display: block;
		width: 30px;
		height: 30px;
	}

	img {
		width: 30px;
		height: 30px;
		border-radius: 50%;
		object-fit: cover;
	}
</style>
