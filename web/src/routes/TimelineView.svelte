<script lang="ts">
	import VirtualList from 'svelte-tiny-virtual-list';
	import NoteView from './NoteView.svelte';
	import type { Timeline } from './types';
	export let timeline: Timeline;
	export let repost: Function;
	export let reaction: Function;
	export let pawPad: boolean;
</script>

<VirtualList itemCount={timeline.events.length} height={600} itemSize={50}>
	<div slot="item" let:index>
		<NoteView event={timeline.events[index]} {repost} {reaction} {pawPad} />
	</div>
</VirtualList>
<!-- <ul>
	{#each timeline.events as event}
		<li>
			<NoteView {event} {repost} {reaction} {pawPad} />
		</li>
	{/each}
</ul> -->

<style>
	ul {
		list-style: none;
		padding: 0;
		border: 1px solid rgb(239, 243, 244);
		border-bottom-style: none;
	}

	li {
		border-bottom: 1px solid rgb(239, 243, 244);
	}
</style>
