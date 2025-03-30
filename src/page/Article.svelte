<script>
  import { onMount } from 'svelte';
  import PocketBase from "pocketbase";
  import {Link} from "svelte5-router";

  let {
    id
  } = $props();

  let entry = $state({});
  const pb = new PocketBase(import.meta.env.VITE_POCKETBASE_URL);

  onMount(async () => {
    const articleOne = await pb.collection("articles").getOne(id);
    entry = articleOne;
  })
</script>

<h1 class="uk-h1">{entry.title}</h1>

<div class="uk-paragraph">
    {@html entry.content}
</div>

<Link to="/articles" class="uk-btn uk-btn-default">⬅️ Back to article list</Link>
