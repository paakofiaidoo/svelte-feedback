<script>
  import Card from "./Card.svelte";
  import { store } from "../stores";
  export let item = {};
  let color = item.rating > 5 ? "green" : "yellow";

  const handleDelete = (id) => {

    store.update((state) => {
      return state.filter((feedback) => feedback.id !== id);
    });
    console.log(id);
  };
</script>

<Card>
  <div class="rating" style="--rating: {color}">
    {item.rating}
  </div>
  <span
    on:click={() => {
      handleDelete(item.id);
    }}>X</span
  >
  <p class="text">
    {item.text}
  </p>
</Card>

<style>
  .rating {
    position: absolute;
    top: -5px;
    left: -5px;
    height: 2rem;
    width: 2rem;
    background-color: var(--rating);
    border-radius: 50%;
    display: flex;
    justify-content: center;
    text-align: center;
    align-items: center;
  }
  span {
    position: absolute;
    top: -5px;
    right: -5px;
    height: 2rem;
    width: 2rem;
    background-color: red;
    border-radius: 50%;
    display: flex;
    justify-content: center;
    text-align: center;
    align-items: center;
  }
</style>
