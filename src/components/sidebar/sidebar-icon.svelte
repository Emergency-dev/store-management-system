<script type="ts">
	export let Icon: any;
	export let title: String = '';
	export let onClick: any = '';
	export let isExpanded: boolean;
</script>

<div
	class="relative flex flex-row h-12 {isExpanded
		? 'w-auto'
		: 'w-12'} items-center justify-around rounded
m-2 text-white text-md p-2 animate-ease-in-out-200
hover:bg-white hover:text-gray-900 hover:cursor-pointer group"
	on:click={onClick}
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
</div>

<!-- 
<p class="relative flex h-12 w-12 items-center justify-center rounded-3xl
 m-2 bg-gray-800 text-green-500
 hover:bg-green-700 hover:rounded hover:text-white
 transition-all group">{icon}

	<span class="absolute left-16 w-auto min-w-max bg-gray-800
	m-2 p-2 rounded-md text-white
	transition-all duration-200 origin-top-left scale-0 group-hover:scale-100">{toolTipText}</span>

</p> -->
