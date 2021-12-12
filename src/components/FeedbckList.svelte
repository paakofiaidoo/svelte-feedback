<script>
  import FeedbackItem from "./FeedbackItem.svelte";
  export let feedback = [];
</script>

<!-- markup (zero or more items) goes here -->
{#each feedback as fb (fb.id)}
  <FeedbackItem item={fb} on:delete-feedback />
{/each}

<style>
  /* your styles go here */
</style>
