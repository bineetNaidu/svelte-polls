<script>
  import Poll from './Poll.svelte';

  // Store
  import PollStore from './store/PollStore.js';

  export let polls = [];

  PollStore.subscribe((data) => {
    polls = data;
  });
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
  {#each polls as poll (poll.id)}
    <Poll {poll} on:vote />
  {/each}
</div>
