<script>
	import Header from "./componets/Header.svelte";
	import Footer from "./componets/Footer.svelte";
	import Tab from "./shared_components/Tabs.svelte";

	//tabs
	let items = ['Current Polls', 'Add New Poll'];
	let activeItem = 'Current Polls';

	const tabChange = (e) => {
		activeItem = e.detail;
	}
</script>


<Header />
<main>
	<Tab {items} {activeItem} on:tabChange={tabChange} />
	{#if activeItem === 'Current Polls'}
		<p>Lista de memes</p>
	{:else if activeItem === 'Add New Poll'}
		<p>Agregar meme</p>
	{/if}
</main>
<Footer />

<style>
	main {
		max-width: 960px;
		margin: 40px auto;
	}
</style> 