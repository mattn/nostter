<script lang="ts">
	import Notification from './Notification.svelte';
	import ReactionEmoji from './ReactionEmoji.svelte';
	import Logout from '../Logout.svelte';
	import { author } from '../../stores/Author';
	import { debugMode } from '../../stores/Preference';
	import WordMute from './WordMute.svelte';
	import AutoRefresh from './AutoRefresh.svelte';
	import MutedUsers from './MutedUsers.svelte';
	import MutedEvents from './MutedEvents.svelte';
	import ClearEmojiMartCache from './ClearEmojiMartCache.svelte';
	import Theme from './Theme.svelte';

	let debugCounter = 0;

	function enableDebugMode() {
		debugCounter++;
		if (debugCounter >= 5) {
			$debugMode = !$debugMode;
			debugCounter = 0;
			console.log('[debug mode]', $debugMode ? 'enabled' : 'disabled');
		}
	}
</script>

<h1>Preference</h1>

{#if $debugMode}
	<Theme />
{/if}
{#if $author !== undefined}
	<div><ReactionEmoji /></div>
	<div>
		<a href="https://emojis-iota.vercel.app/" target="_blank" rel="noopener noreferrer">
			Edit custom emojis
		</a>
	</div>
	<div><MutedUsers /></div>
	<div><MutedEvents /></div>
	<div><WordMute /></div>
{/if}
<div><Notification /></div>
<div><AutoRefresh /></div>
{#if $debugMode}
	<div><ClearEmojiMartCache /></div>
{/if}
<div><Logout /></div>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<h1 on:click={enableDebugMode}>About nostter</h1>
<div>
	<span>GitHub:</span>
	<a href="https://github.com/SnowCait/nostter" target="_blank" rel="noopener noreferrer">
		SnowCait/nostter
	</a>
</div>
<div>
	<span>Author:</span>
	<a href="/npub1s02jksmr6tgmcksf3hnmue7pyzlm0sxwarh7lk8tdeprw2hjg6ysp7fxtw">@SnowCait</a>
</div>
<div>
	<span>Illustration:</span>
	<a href="/npub1e09suzmq9mp6nt0ud9ttl03790qjx70wzwlc2pwwghcusvwju54qs0c800">@stok33</a>
</div>
<img
	src="/nostter-chan.jpg"
	alt=""
	title="前から知っていたような雰囲気ですぐ馴染めるタイプの娘。パーカーの中には json が格納されていて聞くと教えてくれるよ。あとかなり物覚えが良いので昔のことも覚えててくれるよ。"
/>

<style>
	div {
		margin: 1em auto;
	}

	img {
		width: 50%;
		border: 1px solid lightgray;
		border-radius: 10px;
	}
</style>
