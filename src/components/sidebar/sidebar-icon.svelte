<script type="ts">
	export let Icon: any;
	export let title: String = '';
	export let onClick: any = '';
	export let isExpanded: boolean;
	export let isActive: boolean = false;
	export let index: number = -1;
	
	function navigate(){
		onClick(index);
		document.getElementById("navTo-" + index)?.click();
	}
</script>

<div
	class="relative flex flex-row h-12 {isExpanded
		? 'w-auto'
		: 'w-12'} items-center justify-around rounded
m-2 text-md p-2 animate-ease-in-out-200
hover:bg-white hover:text-gray-900 hover:cursor-pointer group
active:bg-white active:text-gray-900
{isActive ? 'text-gray-900 bg-white' : 'text-white'}"
	on:click={navigate}
>
	<svelte:component this={Icon} />
	{#if title != ''}
		{#if !isExpanded}
			<span
				class="absolute left-16 text-white min-w-max p-3 rounded text-sm
	bg-gray-900 shadow-2xl
	animate-ease-in-out-200 scale-0 group-hover:scale-100 origin-left">{title}</span
			>
		{:else}
			<span class="w-96">{title}</span>
		{/if}
	{/if}
	<slot></slot>
</div>