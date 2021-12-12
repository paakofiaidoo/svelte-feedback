<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  import Button from "./Button.svelte";
  import Card from "./Card.svelte";
  import { v4 as uuid } from "uuid";
  let text = "";
  let rating = 10;

  $: disabled = text.trim().length <= 10;
  const handleSubmit = () => {
    if (text.trim().length > 10) {
      let newMessage = {
        id: uuid(),
        text,
        rating,
      };
      dispatch("addMessage", newMessage);

      text = "";
      rating = 10;
    }
  };
</script>

<!-- markup (zero or more items) goes here -->
<form on:submit|preventDefault={handleSubmit}>
  <!-- 10 radio button for rating -->
  <header>
    <h2>Tell us somting about our services</h2>
  </header>
  <ul class="rating">
    {#each Array(10) as _, i}
      <li>
        <input
          type="radio"
          name="rating"
          value={i + 1}
          id="rating-{i + 1}"
          on:change={(e) => {
            rating = i + 1;
            console.log(rating);
          }}
          checked={rating === i + 1}
        />
        <label for="rating-{i + 1}">{i + 1}</label>
      </li>
    {/each}
  </ul>

  <textarea
    name="text"
    id="text"
    cols="20"
    rows="10"
    placeholder="type your feedback here ... "
    bind:value={text}
  />
  {#if disabled & (text.length > 0)}
    <span>text must be more than 10 charaters</span>
  {/if}
  <Button type="submit" style="primary" {disabled}>Send</Button>
</form>

<style>
  /* your styles go here */
  textarea {
    width: 100%;
    height: 100%;
    border-radius: 1rem;
    padding: 1rem;
  }
  .rating {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
  }
  input {
    margin: 0.5rem;
  }
  span {
    color: red;
  }
  li {
    list-style: none;
  }
  .rating {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    margin: auto;
  }
  .rating li {
    position: relative;
    background-color: #ddd;
    width: 2rem;
    height: 2rem;
    border-radius: 50%;
    margin: 0.5rem;
    text-align: center;
    transition: 0.3s;
    border: 1px solid #ccc;
    font-size: 1rem;
    overflow: hidden;
  }
  .rating li label {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    cursor: pointer;
    background-color: transparent;
    border: none;
    color: #000;
  }
  .rating li:hover {
    background-color: #ff6a96;
    color: #fff;
  }
  [type="radio"] {
    opacity: 0;
    display: none;
  }

  [type="radio"]:checked ~ label {
    background-color: #ff6a96;
    color: #fff;
  }
</style>
