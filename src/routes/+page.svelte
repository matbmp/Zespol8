<script lang="ts">
	import { teammates, harmonogram, progress, raports, docs } from '../assets/data';
	import { Step, Stepper } from '@skeletonlabs/skeleton';
	import Account from 'virtual:icons/mdi/account-outline';
	import Pdf from 'virtual:icons/mdi/file-pdf-box';
	import Docs from 'virtual:icons/mdi/book-open-page-variant-outline';
	
</script>

<div class="pagebody">
	<div style:background-image="url(uplash-nurse.jpg)" style:background-position="center">
		<div class="w-full h-full variant-glass">
			<div class="w-full mx-auto p-4">
				<div class=" rounded-2xl p-6 flex flex-wrap items-center justify-center">
					<div class="w-full lg:w-1/2 pb-4">
						<span class="text-6xl lg:text-8xl"> MediCase </span>
						<div class="text-xl lg:text-3xl py-2">
							Aplikacja przeznaczona dla studentów medycyny uczących się przeprowadzać wywiad
							medyczny w obcym języku. Jest oparta na modelu komunikacji <span class="font-bold"
								>Calgary-Cambridge</span
							>, obejmuje
							<span class="text-blue-900 font-semibold">treści tekstowe, audio, oraz video.</span>
							Pozwala na dynamiczne dodawanie i modyfikację treści oraz dostępnych dla użytkownika języków.
							Dodawanie treści jest wspomagane przez
							<span class="font-semibold">sztuczną inteligencję</span>.
						</div>
					</div>
					<div class="hidden lg:flex bg-slate-100 p-4 rounded-2xl h-[52rem]">
						<img src="app2.png" alt="" class="rounded-2xl" />
						<img src="app3.png" alt="" class="rounded-2xl" />
					</div>
				</div>
			</div>
		</div>
	</div>

	<div id="team" class="contain variant-filled-secondary">
		<div class="w-full lg:w-2/3 mx-auto">
			<div class="head">Nasz zespół</div>

			<div class="grid xl:grid-cols-3 md:grid-cols-2 grid-cols-1 lg:gap-12 md:gap-6 gap-3">
				{#each teammates as teammate}
					<div class="flex flex-col card items-center p-4 variant-outline-surface shadow-xl">
						<Account class="text-9xl text-primary" />
						<div class="text-xl font-bold pt-4">{teammate.name}</div>
						<div class="text-lg">{teammate.role}</div>
					</div>
				{/each}
			</div>
		</div>
	</div>

	<div id="harmonogram" class="contain">
		<div class="w-full lg:w-2/3 mx-auto">
			<div class="head">Harmonogram</div>

			<div class="h-[30rem] md:h-[25rem] lg:h-[20rem] flex flex-col">
				<div class="my-auto">
					<Stepper
						stepTerm=""
						buttonBackLabel="←"
						buttonBack="variant-filled shadow text-3xl"
						buttonNextLabel="→"
						buttonNext="variant-filled shadow text-3xl"
						buttonCompleteLabel="Koniec"
					>
						{#each harmonogram as step}
							<Step
								regionHeader="h-60 md:h-40 lg:h-32 text-lg lg:text-xl xl:text-2xl flex flex-col"
								regionContent="text-lg lg:text-2xl badge variant-ringed-surface shadow-lg py-2 px-4"
							>
								<svelte:fragment slot="header"
									><div class="my-auto">{step.title}</div></svelte:fragment
								>
								{step.date}
							</Step>
						{/each}
					</Stepper>
				</div>
			</div>
		</div>
	</div>

	<div id="progress" class="contain">
		<div class="w-full lg:w-2/3 mx-auto">
			<div class="head">Przebieg prac</div>

			<div class="border-l-4 pl-4 border-primary-500 relative">
				{#each progress as step}
					<div class="py-2">
						<div class={`rounded-full h-5 w-5 -ms-7 absolute variant-filled-primary`} />
						<div>
							{#if step.date !== undefined}
								{step.date}
							{/if}
						</div>
						{#if step.title !== undefined}
							<div class="font-bold pb-4">{step.title}</div>
						{/if}
					</div>
				{/each}
			</div>
		</div>
	</div>

	<div id="raports" class="contain variant-filled-secondary">
		<div class="w-full lg:w-2/3 mx-auto">
			<div class="head">Raporty semestralne</div>

			<div class="grid xl:grid-cols-3 md:grid-cols-2 grid-cols-1 lg:gap-12 md:gap-6 gap-3">
				{#each raports as raport}
					<a
						href={raport.download}
						download={raport.download}
						class="flex flex-col card items-center p-4 variant-outline-primary shadow-lg"
					>
						<Pdf class="text-9xl text-surface" />
						{raport.name}
					</a>
				{/each}
			</div>
		</div>
	</div>

	<div id="docs" class="contain">
		<div class="w-full lg:w-2/3 mx-auto">
			<div class="head">Dokumentacja</div>

			<div class="grid xl:grid-cols-2 md:grid-cols-2 grid-cols-1 lg:gap-12 md:gap-6 gap-3">
				{#each docs as doc}
					<a
						href={doc.download}
						download={doc.download}
						class="flex flex-col card items-center p-4 variant-outline-primary shadow-lg"
					>
						<Docs class="text-9xl text-surface" />
						{doc.name}
					</a>
				{/each}
			</div>
		</div>
	</div>
</div>

<style lang="postcss">
	.pagebody {
		overflow-y: auto;
		scroll-behavior: smooth;
	}
	.contain {
		@apply shadow-lg py-6 lg:py-16 px-2;
	}
	.head {
		@apply flex justify-center text-4xl lg:text-6xl pb-12;
	}

	.contain2 {
	}
</style>
