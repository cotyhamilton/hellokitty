<script lang="ts">
	import Todo from "./Todo.svelte";
	import * as DropdownMenu from "$lib/components/ui/dropdown-menu/index.js";
	import { buttonVariants } from "$lib/components/ui/button/index.js";
	import { CircleX, Settings } from "@lucide/svelte";
	import type { SvelteComponent } from "svelte";

	interface TodoComponent extends SvelteComponent {
		clear: () => void;
	}

	let children: Partial<Record<string, TodoComponent>> = {};

	const clear = () => {
		Object.values(children).forEach((child) => child?.clear());
	};
</script>

<div class="min-h-screen bg-gray-50 p-4 pb-16">
	<header class="mx-auto max-w-5xl">
		<img
			src="/images/logo.png"
			alt="Hello Kitty Island Adventure Logo"
			class="mx-auto w-full max-w-sm sm:max-w-lg"
		/>
	</header>

	<div class="mx-auto flex max-w-5xl justify-end px-4 sm:px-6 lg:px-8">
		<DropdownMenu.Root>
			<DropdownMenu.Trigger
				class={`${buttonVariants({ variant: "outline" })} border-gray-200 bg-gray-50 hover:border-gray-300`}
			>
				<Settings />
			</DropdownMenu.Trigger>
			<DropdownMenu.Content class="w-56">
				<DropdownMenu.Item class="cursor-pointer" onclick={clear}>
					<CircleX class="mr-2 size-4" />
					<span>Clear</span>
				</DropdownMenu.Item>
			</DropdownMenu.Content>
		</DropdownMenu.Root>
	</div>

	<main class="mx-auto max-w-5xl px-4 py-6 sm:px-6 lg:px-8">
		<ul class="space-y-3">
			<Todo key="hello-kitty" bind:this={children["hello-kitty"]}>
				{#snippet text()}
					<img class="thumb" src="/images/small/Hello_Kitty.png" alt="" />
					<strong>Hello Kitty</strong>
				{/snippet}

				{#snippet details()}
					<a
						href="https://hellokittyislandadventure.wiki.gg/wiki/Hello_Kitty#Liked_Gifts"
						target="_blank">Liked gifts</a
					>
				{/snippet}
			</Todo>
			<Todo key="badtz-maru" bind:this={children["badtz-maru"]}>
				{#snippet text()}
					<img class="thumb" src="/images/small/Badtz-maru.png" alt="" />
					<strong>Badtz-Maru</strong>
				{/snippet}

				{#snippet details()}
					<a
						href="https://hellokittyislandadventure.wiki.gg/wiki/Badtz-maru#Liked_Gifts"
						target="_blank">Liked gifts</a
					>
				{/snippet}
			</Todo>
			<Todo key="chococat" bind:this={children["chococat"]}>
				{#snippet text()}
					<img class="thumb" src="/images/small/Chococat.png" alt="" />
					<strong>Chococat</strong>
				{/snippet}

				{#snippet details()}
					<a
						href="https://hellokittyislandadventure.wiki.gg/wiki/Chococat#Liked_Gifts"
						target="_blank">Liked gifts</a
					>
				{/snippet}
			</Todo>
			<Todo key="cinnamoroll" bind:this={children["cinnamoroll"]}>
				{#snippet text()}
					<img class="thumb" src="/images/small/Cinnamoroll.png" alt="" />
					<strong>Cinnamoroll</strong>
				{/snippet}

				{#snippet details()}
					<a
						href="https://hellokittyislandadventure.wiki.gg/wiki/Cinnamoroll#Liked_Gifts"
						target="_blank">Liked gifts</a
					>
				{/snippet}
			</Todo>
			<Todo key="hangyodon" bind:this={children["hangyodon"]}>
				{#snippet text()}
					<img class="thumb" src="/images/small/Hangyodon.png" alt="" />
					<strong>Hangyodon</strong>
				{/snippet}

				{#snippet details()}
					<a
						href="https://hellokittyislandadventure.wiki.gg/wiki/Hangyodon#Liked_Gifts"
						target="_blank">Liked gifts</a
					>
				{/snippet}
			</Todo>
			<Todo key="keroppi" bind:this={children["keroppi"]}>
				{#snippet text()}
					<img class="thumb" src="/images/small/Keroppi.png" alt="" />
					<strong>Keroppi</strong>
				{/snippet}

				{#snippet details()}
					<a
						href="https://hellokittyislandadventure.wiki.gg/wiki/Keroppi#Liked_Gifts"
						target="_blank">Liked gifts</a
					>
				{/snippet}
			</Todo>
			<Todo key="kuromi" bind:this={children["kuromi"]}>
				{#snippet text()}
					<img class="thumb" src="/images/small/Kuromi.png" alt="" />
					<strong>Kuromi</strong>
				{/snippet}

				{#snippet details()}
					<a
						href="https://hellokittyislandadventure.wiki.gg/wiki/Kuromi#Liked_Gifts"
						target="_blank">Liked gifts</a
					>
				{/snippet}
			</Todo>
			<Todo key="my_melody" bind:this={children["my_melody"]}>
				{#snippet text()}
					<img class="thumb" src="/images/small/My_Melody.png" alt="" />
					<strong>My Melody</strong>
				{/snippet}

				{#snippet details()}
					<a
						href="https://hellokittyislandadventure.wiki.gg/wiki/My_Melody#Liked_Gifts"
						target="_blank">Liked gifts</a
					>
				{/snippet}
			</Todo>
			<Todo key="pekkle" bind:this={children["pekkle"]}>
				{#snippet text()}
					<img class="thumb" src="/images/small/Pekkle.png" alt="" />
					<strong>Pekkle</strong>
				{/snippet}

				{#snippet details()}
					<a
						href="https://hellokittyislandadventure.wiki.gg/wiki/Pekkle#Liked_Gifts"
						target="_blank">Liked gifts</a
					>
				{/snippet}
			</Todo>
			<Todo key="pochacco" bind:this={children["pochacco"]}>
				{#snippet text()}
					<img class="thumb" src="/images/small/Pochacco.png" alt="" />
					<strong>Pochacco</strong>
				{/snippet}

				{#snippet details()}
					<a
						href="https://hellokittyislandadventure.wiki.gg/wiki/Pochacco#Liked_Gifts"
						target="_blank">Liked gifts</a
					>
				{/snippet}
			</Todo>
			<Todo key="pompompurin" bind:this={children["pompompurin"]}>
				{#snippet text()}
					<img class="thumb" src="/images/small/Pompompurin.png" alt="" />
					<strong>Pompompurin</strong>
				{/snippet}

				{#snippet details()}
					<a
						href="https://hellokittyislandadventure.wiki.gg/wiki/Pompompurin#Liked_Gifts"
						target="_blank">Liked gifts</a
					>
				{/snippet}
			</Todo>
			<Todo key="retsuko" bind:this={children["retsuko"]}>
				{#snippet text()}
					<img class="thumb" src="/images/small/Retsuko.png" alt="" />
					<strong>Retsuko</strong>
				{/snippet}

				{#snippet details()}
					<a
						href="https://hellokittyislandadventure.wiki.gg/wiki/Retsuko#Liked_Gifts"
						target="_blank">Liked gifts</a
					>
				{/snippet}
			</Todo>
			<Todo key="tuxedosam" bind:this={children["tuxedosam"]}>
				{#snippet text()}
					<img class="thumb" src="/images/small/Tuxedosam.png" alt="" />
					<strong>Tuxedo Sam</strong>
				{/snippet}

				{#snippet details()}
					<a
						href="https://hellokittyislandadventure.wiki.gg/wiki/Tuxedo_Sam#Liked_Gifts"
						target="_blank">Liked gifts</a
					>
				{/snippet}
			</Todo>
		</ul>
	</main>
</div>

<style>
	a {
		color: #007bff;
		text-decoration: none;
		font-weight: bold;
	}

	.thumb {
		height: 20px;
		display: inline;
	}
</style>
