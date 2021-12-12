<script>
  import { store } from "../stores";
  import { fade, scale } from "svelte/transition";
  import FeedbackItem from "./FeedbackItem.svelte";
  let feedback = [];

  // store.subscribe((data) => {
  //   feedback = data;
  // });
</script>

<!-- markup (zero or more items) goes here -->
{#each $store as fb (fb.id)}
  <div in:scale out:fade>
    <FeedbackItem item={fb} />
  </div>
{/each}

<style>
  /* your styles go here */
</style>
