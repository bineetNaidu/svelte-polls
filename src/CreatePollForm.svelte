<script>
  import { createEventDispatcher } from 'svelte';
  import Button from './Button.svelte';
  import PollStore from './store/PollStore';

  const dispatch = createEventDispatcher();

  let field = { question: '', answerA: '', answerB: '' };
  let errors = { question: '', answerA: '', answerB: '' };
  let valid = false;

  const handleSubmit = () => {
    valid = true;
    // validate question
    if (field.question.trim().length < 5) {
      valid = false;
      errors.question = 'Question must be at least 5 character long';
    } else {
      errors.question = '';
    }
    // validate answer A
    if (field.answerA.trim().length < 1) {
      valid = false;
      errors.answerA = 'answerA must be at least 1 character long';
    } else {
      errors.answerA = '';
    }
    // validate answer A
    if (field.answerB.trim().length < 1) {
      valid = false;
      errors.answerB = 'answerB must be at least 1 character long';
    } else {
      errors.answerB = '';
    }

    // add new poll
    if (valid) {
      let poll = { ...field, id: Math.random(), votesA: 0, votesB: 0 };
      // save poll to store
      PollStore.update((currPolls) => {
        return [poll, ...currPolls];
      });
      dispatch('addPoll');
    }
  };
</script>

<style>
  form {
    width: 400px;
    margin: 0 auto;
    text-align: center;
  }

  .form-field {
    margin: 18px auto;
  }

  input {
    width: 100%;
    border-radius: 6px;
  }

  label {
    margin: 10px auto;
    text-align: left;
  }

  .error {
    font-weight: bold;
    font-size: 12px;
    color: #d91b42;
  }
</style>

<form on:submit|preventDefault={handleSubmit}>
  <div class="form-field">
    <label for="question">Poll Question:</label>
    <input type="text" id="question" bind:value={field.question} />
    <div class="error">{errors.question}</div>
  </div>

  <div class="form-field">
    <label for="answer-a">Answer A:</label>
    <input type="text" id="answer-a" bind:value={field.answerA} />
    <div class="error">{errors.answerA}</div>
  </div>

  <div class="form-field">
    <label for="answer-b">Answer B:</label>
    <input type="text" id="answer-b" bind:value={field.answerB} />
    <div class="error">{errors.answerB}</div>
  </div>

  <Button type="secondary" flat>Add Poll</Button>
</form>
