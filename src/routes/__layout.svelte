<script>
	import '../app.css';
	import Sidebar from '../components/sidebar/sidebar.svelte';
</script>


<div class="flex flex-row">
	<Sidebar></Sidebar>
	<div class="w-full">
		<slot />
	</div>
	
</div>



