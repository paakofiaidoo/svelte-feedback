<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();
  export let style = "primary",
    type = "button",
    disabled = true;
</script>

<!-- markup (zero or more items) goes here -->
<button
  {disabled}
  {type}
  on:click={() => {
    dispatch("");
  }}
  class={style}
>
  <slot />
</button>

<style>
  button {
    padding: 1rem;
    width: auto;
    height: 100%;
    margin: 1rem auto;
    border: none;
    border-radius: 1rem;
    font-weight: bolder;
    cursor: pointer;
    margin-right: 0;
  }
  .primary {
    background-color: #0000ff50;
    color: #ff0;
  }
  .primary:hover {
    background-color: #0000ff70;
  }
  .secondary {
    background-color: greenyellow;
    color: #000;
  }

  button:disabled {
    background-color: #ddd;
    color: #666;
    cursor: auto;
  }
  button:disabled:hover {
    background-color: #ddd;
  }
</style>
