<script type="ts">
	import IoIosMenu from 'svelte-icons/io/IoIosMenu.svelte';
	import FaCashRegister from 'svelte-icons/fa/FaCashRegister.svelte';
	import FaBoxOpen from 'svelte-icons/fa/FaBoxOpen.svelte';
	import FaUserCog from 'svelte-icons/fa/FaUserCog.svelte';
	import MdExitToApp from 'svelte-icons/md/MdExitToApp.svelte';
	import TiArrowLeft from 'svelte-icons/ti/TiArrowLeft.svelte';
	import SidebarIcon from './sidebar-icon.svelte';

	export let expanded: boolean = false;
	export let toggle: any;

	function switchActive(iconIndex: number) {
		for (let index = 0; index < icons.length; index++) {
			const element = icons[index];
			element.isActive = false;
		}

		icons[iconIndex].isActive = true;
	}

	let icons: sidebarIcon[] = [
		{ index: 0, icon: FaCashRegister, title: 'Point of Sale', isActive: false,  href: "/point-of-sale/home" },
		{ index: 1, icon: FaBoxOpen, title: 'Inventory', isActive: false, href: "/inventory/home" },
		{ index: 2, icon: FaUserCog, title: 'User Management', isActive: false, href: "/user-management/home" }
	];

	interface sidebarIcon {
		index: number;
		icon: any;
		title: string;
		isActive: boolean;
		href: string;
	}
</script>

<div
	class="fixed h-screen {expanded ? 'w-64' : 'w-16'} flex flex-col justify-between m-0 left-0
        bg-gray-900 text-white animate-ease-in-out-200"
>
	<div class="flex flex-col">
		<div class="flex justify-end">
			<SidebarIcon
				isExpanded={expanded}
				Icon={expanded ? TiArrowLeft : IoIosMenu}
				onClick={toggle}
			/>
		</div>
		<div class="border m-2" />
		{#each icons as iconElement}
			<SidebarIcon
				index={iconElement.index}
				onClick={switchActive}
				isActive={iconElement.isActive}
				isExpanded={expanded}
				Icon={iconElement.icon}
				title={iconElement.title}
			>
				<a href={iconElement.href} id="navTo-{iconElement.index}" hidden>1</a>
			</SidebarIcon>
		{/each}
	</div>
	<div class="flex flex-col">
		<SidebarIcon isExpanded={expanded} Icon={MdExitToApp} title="Logout" />
	</div>
</div>
