<script lang="ts">
	import { Popover } from '@skeletonlabs/skeleton-svelte';
	import IconX from '@lucide/svelte/icons/x';

	let openState = $state(false);

	function popoverOpen() {
		openState = true;
	}

	function popoverClose() {
		openState = false;
	}

	// function popoverToggle() {
	// 	openState = !openState;
	// }
	// setInterval(popoverToggle, 3000);
</script>

<div class="space-y-10">
	<header>
		<h1 class="h1">Popovers</h1>
	</header>
	<aside class="card preset-tonal-warning p-4 text-center">
		<!-- prettier-ignore -->
		<p>This component is available only for Svelte. It will remain until <a href="https://floating-ui-svelte.vercel.app/" target="_blank" class="underline">Floating UI Svelte</a> ready for production.</p>
	</aside>
	<section class="grid grid-cols-[1fr_auto] items-center gap-4">
		<pre class="pre">{JSON.stringify(openState, null, 2)}</pre>
		<button class="btn preset-filled" onclick={popoverOpen} disabled={openState}>Open Popover</button>
	</section>
	<section class="border border-surface-200-800 space-y-4 p-20 flex justify-center items-center">
		<Popover
			open={openState}
			onOpenChange={(e) => (openState = e.open)}
			positioning={{ placement: 'bottom', offset: { mainAxis: 20 } }}
			triggerBase="btn preset-tonal"
			contentBase="card bg-surface-200-800 p-4 space-y-4 max-w-[320px]"
			arrow
			arrowBackground="var(--color-surface-200-800)"
		>
			{#snippet trigger()}Click Me{/snippet}
			{#snippet content()}
				<header class="flex justify-between">
					<p class="font-bold text-xl">Popover</p>
					<button class="btn-icon" onclick={popoverClose}>
						<IconX />
					</button>
				</header>
				<article>
					<p class="opacity-60">
						Lorem ipsum dolor, sit amet consectetur adipisicing elit. Minima aut odio maxime placeat quia eligendi distinctio.
					</p>
				</article>
			{/snippet}
		</Popover>
	</section>
</div>
