<script lang="ts">
	import Icon from 'virtual:icons/mdi/rocket-launch-outline';
	import type { PopupSettings } from '@skeletonlabs/skeleton';
	import { popup } from '@skeletonlabs/skeleton';

	const popupClick: PopupSettings = {
		event: 'click',
		target: 'popupClick',
		placement: 'top'
	};
</script>

<div class="p-4 text-lg">
	<h1 class="text-2xl">Welcome to SvelteKit</h1>
	This template includes:
	<ul>
		<li class="my-2">
			<button class="rounded-xl bg-blue-400 text-white p-2 px-4">Tailwind</button>
		</li>
		<li><button class="btn variant-filled" use:popup={popupClick}>SkeletonUI with Floating UI</button></li>
		<li>unplugin-icons with Material Design Icon pack <Icon class="inline-block w-10 h-10" /></li>
	</ul>
</div>

<div class="card p-4 variant-filled-primary" data-popup="popupClick">
	<p>Click Content</p>
	<div class="arrow variant-filled-primary" />
</div>
