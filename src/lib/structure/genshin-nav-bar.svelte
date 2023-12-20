<script>
	import { page } from '$app/stores';
	import { Navbar, NavBrand, NavLi, NavUl, NavHamburger } from 'flowbite-svelte';

	$: activeUrl = $page.url.pathname;
</script>

<Navbar>
	<NavBrand>
		<span class="self-center whitespace-nowrap text-xl font-semibold dark:text-white"
			>Genshin Utilities</span
		>
	</NavBrand>
	<NavHamburger />
	<NavUl {activeUrl}>
		<NavLi>
			<a href="/">Home</a>
		</NavLi>
		<NavLi>
			<a href="/">About</a>
		</NavLi>
		<NavLi>
			<a href="/">Contact</a>
		</NavLi>
	</NavUl>
</Navbar>
