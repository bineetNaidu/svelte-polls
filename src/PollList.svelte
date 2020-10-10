<script>
  import Poll from './Poll.svelte';

  export let polls = [];
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
