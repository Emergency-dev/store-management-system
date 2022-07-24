<script type="ts">
	import IoIosMenu from 'svelte-icons/io/IoIosMenu.svelte';
	import FaCashRegister from 'svelte-icons/fa/FaCashRegister.svelte';
	import FaBoxOpen from 'svelte-icons/fa/FaBoxOpen.svelte';
	import FaUserCog from 'svelte-icons/fa/FaUserCog.svelte';
    import MdExitToApp from 'svelte-icons/md/MdExitToApp.svelte';
    import TiArrowLeft from 'svelte-icons/ti/TiArrowLeft.svelte';
	import SidebarIcon from './sidebar-icon.svelte';

    export let expanded:boolean = false;
    export let toggle:any;
</script>

<div
	class="fixed h-screen {expanded ? 'w-64' : 'w-16'} flex flex-col justify-between m-0 left-0
        bg-gray-900 text-white animate-ease-in-out-200"
>
	<div class="flex flex-col">
        <div class="flex justify-end">
            <SidebarIcon isExpanded={expanded} Icon={expanded ? TiArrowLeft : IoIosMenu} onClick={toggle} />
        </div>
		<div class="border m-2" />
		<SidebarIcon isExpanded={expanded} Icon={FaCashRegister} title={'Point of Sale'} />
		<SidebarIcon isExpanded={expanded} Icon={FaBoxOpen} title="Inventory" />
		<SidebarIcon isExpanded={expanded} Icon={FaUserCog} title="User Management" />
	</div>
    <div class="flex flex-col">
        <SidebarIcon isExpanded={expanded} Icon={MdExitToApp} title="Logout" />
    </div>
</div>