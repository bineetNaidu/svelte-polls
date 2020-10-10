<script>
  import Footer from './Footer.svelte';
  import Header from './Header.svelte';
  import Tabs from './Tabs.svelte';
  import CreatePollForm from './CreatePollForm.svelte';

  // Tabs
  let items = ['Current Polls', 'Add New Poll'];
  let activeItem = 'Current Polls';
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
    <p>THe polls to show</p>
  {:else if activeItem === 'Add New Poll'}
    <CreatePollForm />
  {/if}
</main>
<Footer />
