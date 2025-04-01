<script lang="ts">
	import { browser } from "$app/environment";
	import { Check, ChevronDown, Info } from "@lucide/svelte";
	import type { Snippet } from "svelte";

	interface Props {
		key: string;
		text: Snippet;
		details?: Snippet;
	}

	let { text, details, key }: Props = $props();
	let completed = $state((browser && localStorage.getItem(`todo-${key}`) === "true") || false);

	export const clear = () => {
		completed = false;
	};

	$effect(() => {
		localStorage.setItem(`todo-${key}`, completed.toString());
	});
</script>

<!-- update additional tabs and windows -->
<svelte:window
	onstorage={(event) => {
		if (event.key === `todo-${key}`) {
			completed = event.newValue === "true";
		}
	}}
/>

<li
	class="rounded-xl border transition-all duration-200 {completed
		? 'border-green-200 bg-green-50'
		: 'border-gray-200 bg-gray-50 hover:border-gray-300'}"
>
	{#if details}
		<details class="group">
			<summary class="flex cursor-pointer items-center p-4 sm:p-5">
				<button
					class="mr-4 flex h-6 w-6 flex-shrink-0 cursor-pointer items-center justify-center rounded-md border transition-colors duration-200 {completed
						? 'border-green-500 bg-green-500'
						: 'border-gray-300 hover:border-green-400'}"
					aria-label={completed ? "Mark as incomplete" : "Mark as complete"}
					onclick={() => (completed = !completed)}
				>
					{#if completed}
						<Check class="h-4 w-4 text-white" />
					{/if}
				</button>

				<span
					class="flex-grow text-base transition-colors duration-200 {completed
						? 'text-green-700 line-through'
						: 'text-gray-700'}"
				>
					{@render text()}
				</span>

				<div
					class="ml-2 flex items-center text-gray-400 transition-colors group-hover:text-gray-600"
				>
					<Info class="mr-1 h-4 w-4" />
					<ChevronDown class="h-4 w-4 transition-transform duration-200 group-open:rotate-180" />
				</div>
			</summary>

			<div class="px-4 pb-4">
				<div class="flex">
					<p class="text-sm text-gray-600">{@render details()}</p>
				</div>
			</div>
		</details>
	{:else}
		<div class="flex items-center p-4 sm:p-5">
			<button
				class="mr-4 flex h-6 w-6 flex-shrink-0 items-center justify-center rounded-md border transition-colors duration-200 {completed
					? 'border-green-500 bg-green-500'
					: 'border-gray-300 hover:border-green-400'}"
				aria-label={completed ? "Mark as incomplete" : "Mark as complete"}
				onclick={() => (completed = !completed)}
			>
				{#if completed}
					<Check class="h-4 w-4 text-white" />
				{/if}
			</button>

			<span
				class="flex-grow text-base transition-colors duration-200 {completed
					? 'text-green-700 line-through'
					: 'text-gray-700'}"
			>
				{@render text()}
			</span>
		</div>
	{/if}
</li>

<style>
	details > summary::marker,
	details > summary::-webkit-details-marker {
		display: none;
	}
</style>
