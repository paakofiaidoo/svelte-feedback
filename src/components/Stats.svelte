<script>
  import { store } from "../stores";

  $: count = $store.length;
  $: average = (
    $store.reduce((a, b) => a + b.rating, 0) / $store.length
  ).toFixed(1);
</script>

<div class="stat">
  <h4>{count} Reviews</h4>
  <h4>Rating Average: {average}</h4>
</div>

<style>
  .stat {
    display: flex;
    justify-content: space-between;
  }
</style>
