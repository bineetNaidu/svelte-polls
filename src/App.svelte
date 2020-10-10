<script>
  import Footer from './Footer.svelte';
  import Header from './Header.svelte';
  import Tabs from './Tabs.svelte';

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
  <h1>Hello, Pollers</h1>
</main>
<Footer />
