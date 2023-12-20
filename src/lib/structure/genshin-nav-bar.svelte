<script>
	import { page } from '$app/stores';
	import { Navbar, NavBrand, NavLi, NavUl, NavHamburger } from 'flowbite-svelte';

	$: activeUrl = $page.url.pathname;
</script>

<Navbar rounded class="bg-light-sky">
	<NavBrand>
		<span class="self-center whitespace-nowrap text-xl font-semibold text-pearl"
			>Genshin Utilities</span
		>
	</NavBrand>
	<NavHamburger />
	<NavUl {activeUrl}>
		<NavLi class="text-pearl">
			<a href="/" class="hover:text-dark-pearl font-family:Genshin">Home</a>
		</NavLi>
		<NavLi class="text-pearl">
			<a href="/critcalculator" class="hover:text-dark-pearl">Crit Calculator</a>
		</NavLi>
		<NavLi class="text-pearl">
			<a href="/" class="hover:text-dark-pearl">About</a>
		</NavLi>
	</NavUl>
</Navbar>
