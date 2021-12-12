<script>
  import { fade, scale } from "svelte/transition";
  import FeedbackItem from "./FeedbackItem.svelte";
  export let feedback = [];
</script>

<!-- markup (zero or more items) goes here -->
{#each feedback as fb (fb.id)}
  <div in:scale out:fade>
    <FeedbackItem item={fb} on:delete-feedback />
  </div>
{/each}

<style>
  /* your styles go here */
</style>
