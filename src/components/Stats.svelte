<script>
  export let count = 0,
    average = 0;
</script>

<div class="stat">
  <h4>{count} Reviews</h4>
  <h4>Rating Average: {average}</h4>
</div>

<style>
  .stat{
      display: flex;
      justify-content: space-between;
  }
</style>
