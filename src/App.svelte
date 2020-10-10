<script>
  import Footer from './Footer.svelte';
  import Header from './Header.svelte';
  import Tabs from './Tabs.svelte';
  import CreatePollForm from './CreatePollForm.svelte';
  import PollList from './PollList.svelte';

  // Tabs
  let items = ['Current Polls', 'Add New Poll'];
  let activeItem = 'Current Polls';

  // Functions
  const handleAdd = (e) => (activeItem = 'Current Polls');
</script>

<style>
  main {
    max-width: 960px;
    margin: 40px auto;
  }
</style>

<Header />
<main>
  <Tabs {items} {activeItem} on:setTabs={(e) => (activeItem = e.detail)} />
  {#if activeItem === 'Current Polls'}
    <PollList />
  {:else if activeItem === 'Add New Poll'}
    <CreatePollForm on:addPoll={handleAdd} />
  {/if}
</main>
<Footer />
