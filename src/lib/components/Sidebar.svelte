<script lang="ts">
	import { Nav_Buttons, Profile_Menu } from '$lib/data';
	import { LightSwitch } from '@skeletonlabs/skeleton';
	import { faker } from '@faker-js/faker';
	import { popup } from '@skeletonlabs/skeleton';
	import type { PopupSettings } from '@skeletonlabs/skeleton';

	import logo from '$lib/assets/images/logo.ico';

	const popupFeatured: PopupSettings = {
		// Represents the type of event that opens/closed the popup
		event: 'click',
		// Matches the data-popup value on your popup element
		target: 'popupFeatured',
		// Defines which side of your trigger the popup will appear
		placement: 'right-end'
	};

	// State
	let selected = 0;
</script>

<div class="box-shadow h-screen w-[100px] p-4">
	<div class="flex flex-col items-center justify-between h-full space-y-6">
		<div class="items-center space-y-8">
			<div class="h-[64px] w-[64px] rounded-[12px] bg-primary-700">
				<img src={logo} alt="logo" />
			</div>
			<div class="flex flex-col items-center h-full mx-auto space-y-6 w-max">
				{#each Nav_Buttons as button, index}
					{#if index === selected}
						<div class="p-2 bg-primary-700 rounded-[12px]">
							<button type="button" class="text-2xl text-white btn-icon"
								><svelte:component this={button.icon} /></button
							>
						</div>
					{:else}
						<button type="button" class="text-2xl btn-icon" on:click={() => (selected = index)}
							><svelte:component this={button.icon} /></button
						>
					{/if}
				{/each}
			</div>
		</div>
		<div class="flex flex-col items-center p-4 space-y-8">
			<LightSwitch />
			<button type="button" use:popup={popupFeatured}>
				<img
					src={faker.image.avatar()}
					alt="profile pic"
					class="rounded-full btn-icon variant-filled-primary"
				/>
			</button>
		</div>
	</div>
</div>
<div class="flex flex-col w-40 p-2 bg-white card" data-popup="popupFeatured">
	{#each Profile_Menu as menuItem}
		<button
			type="button"
			class="flex justify-between w-full py-1.5 rounded-md btn hover:bg-gray-300"
		>
			<span class="text-sm">{menuItem.title}</span>
			<svelte:component this={menuItem.icon} />
		</button>
	{/each}
</div>

<style>
	.box-shadow {
		box-shadow: 0 0 2px rgba(0, 0, 0, 0.25);
	}
</style>
