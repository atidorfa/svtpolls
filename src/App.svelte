<script>
	import Header from "./componets/Header.svelte";
	import Footer from "./componets/Footer.svelte";
	import CreatePollForm from "./componets/CreatePollForm.svelte";
	import PollList from "./componets/PollList.svelte";
	import Tabs from "./shared_components/Tabs.svelte";

	// tabs
	let items = ['Current Polls', 'Add New Poll'];
	let activeItem = 'Current Polls';

	const tabChange = (e) => {
		activeItem = e.detail;
	}

	// polls
	let polls = [
		{
			id: 1,
			question: 'Python or Javascript?',
			answerA: 'Python',
			answerB: 'Javascript',
			votesA: 15,
			votesB: 9
		},
	];

	const handleAdd = (e) => {
		const poll = e.detail;
		polls = [poll, ...polls]
		console.log(polls)
		activeItem = 'Current Polls'
	}
</script>


<Header />
<main>
	<Tabs {items} {activeItem} on:tabChange={tabChange} />
	{#if activeItem === 'Current Polls'}
		<PollList {polls} />
	{:else if activeItem === 'Add New Poll'}
		<CreatePollForm on:add={handleAdd}/>
	{/if}
</main>
<Footer />

<style>
	main {
		max-width: 960px;
		margin: 40px auto;
	}
</style> 