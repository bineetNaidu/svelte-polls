<script>
  import Footer from './Footer.svelte';
  import Header from './Header.svelte';
  import Tabs from './Tabs.svelte';
  import CreatePollForm from './CreatePollForm.svelte';
  import PollList from './PollList.svelte';

  // Tabs
  let items = ['Current Polls', 'Add New Poll'];
  let activeItem = 'Current Polls';

  // polls
  let polls = [
    {
      id: 1,
      question: 'Python or JavaScript?',
      answerA: 'Python',
      answerB: 'JavaScript',
      votesA: 9,
      votesB: 15,
    },
  ];

  // Functions
  const handleAdd = (e) => {
    const poll = e.detail;
    polls = [poll, ...polls];
    activeItem = 'Current Polls';
  };

  const handleVotes = (e) => {
    const { id, option } = e.detail;
    let copiedPolls = [...polls];
    let upvotedPoll = copiedPolls.find((poll) => poll.id === id);
    if (option === 'a') {
      upvotedPoll.votesA++;
    } else if (option === 'b') {
      upvotedPoll.votesB++;
    }

    polls = copiedPolls;
  };
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
    <PollList {polls} on:vote={handleVotes} />
  {:else if activeItem === 'Add New Poll'}
    <CreatePollForm on:addPoll={handleAdd} />
  {/if}
</main>
<Footer />
