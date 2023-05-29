<script lang="ts">
	import '../theme.css';
	//import '@skeletonlabs/skeleton/themes/theme-skeleton.css';

	// This contains the bulk of Skeletons required styles:
	// NOTE: this will be renamed skeleton.css in the v2.x release.
	import '@skeletonlabs/skeleton/styles/skeleton.css';

	// Finally, your application's global stylesheet (sometimes labeled 'app.css')
	import '../app.postcss';

	import { computePosition, autoUpdate, offset, shift, flip, arrow } from '@floating-ui/dom';
	import { AppBar, AppShell, storePopup } from '@skeletonlabs/skeleton';
	storePopup.set({ computePosition, autoUpdate, offset, shift, flip, arrow });

	const buttons = [
		{
			text: 'Zespół',
			href: '#team'
		},
		{
			text: 'Harmonogram',
			href: '#harmonogram'
		},
		{
			text: 'Przebieg',
			href: '#progress'
		},
		{
			text: 'Raporty',
			href: '#raports'
		},
		{
			text: 'Dokumentacja',
			href: '#docs'
		}
	];
</script>

<AppShell slotHeader="shadow-lg sticky top-0 z-10">
	<svelte:fragment slot="header">
		<AppBar>
			<svelte:fragment slot="lead">
				<img src="/umk.svg" alt="" width="40" height="40" />
			</svelte:fragment>
			Programowanie zespołowe - zespół 8
			<svelte:fragment slot="trail">
				<div class="hidden lg:block">
					{#each buttons as button}
						<a
							href={button.href}
							class="btn mx-2 variant-filled-primary"
							on:click={(e) =>
								document
									.getElementById(new URL(e.currentTarget.href).hash.replace('#', ''))
									?.scrollIntoView({behavior: 'smooth'}, )}
						>
							{button.text}
						</a>
					{/each}
				</div>
			</svelte:fragment>
		</AppBar>
	</svelte:fragment>

	<slot />
</AppShell>
