<script type="ts">
	import '../app.css';
	import Sidebar from '../components/sidebar/sidebar.svelte';

	let expanded:boolean = false;

    $: outerWidth = 0

    $: {
        if(outerWidth < 1280){
            expanded = false;
        }
    }

	function toggle(){
        if(outerWidth > 1280){
            expanded = !expanded;
        }
    }
</script>

<svelte:window bind:outerWidth/>

<div class="flex flex-row">
	<Sidebar expanded={expanded} toggle={toggle}></Sidebar>
	
	<div class="bg-white flex-grow {expanded ? 'ml-64' : 'ml-16'}
	animate-ease-in-out-200">
		<slot />
	</div>
	
</div>



