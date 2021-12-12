<script>
  import { store } from "./stores";
  import FeedbackList from "./components/FeedbckList.svelte";
  import Stats from "./components/Stats.svelte";
  import Form from "./components/Form.svelte";
  import Card from "./components/Card.svelte";

  //   store.subscribe((data) => {
  //     feedback = data;
  //   });

  const addMessage = (e) => {
    store.update((state) => [e.detail, ...state]);
    // feedback = [e.detail, ...feedback];
  };
</script>

<main>
  <Card>
    <Form on:addMessage={addMessage} />
  </Card>

  <Stats />
  <FeedbackList />
</main>

<style>
</style>
