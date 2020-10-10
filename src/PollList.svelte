<script>
  // import { onDestroy, onMount } from 'svelte';
  import Poll from './Poll.svelte';

  // Store
  import PollStore from './store/PollStore.js';

  // export let polls = [];

  // const unSub = PollStore.subscribe((data) => {
  //   polls = data;
  // });

  // onDestroy(() => {
  //   unSub();
  // });
</script>

<style>
  .poll-list {
    display: grid;
    grid-template-columns: 1fr 1fr;
    row-gap: 20px;
    column-gap: 20px;
  }
</style>

<div class="poll-list">
  {#each $PollStore as poll (poll.id)}
    <Poll {poll} />
  {/each}
</div>
