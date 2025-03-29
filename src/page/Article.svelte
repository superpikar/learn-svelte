<script>
  import { onMount } from 'svelte';
  import MainMenu from "../lib/MainMenu.svelte";
  import PocketBase from "pocketbase";
  import {Link} from "svelte5-router";

  let { id } = $props();

  let entry = $state({});
  const pb = new PocketBase(import.meta.env.VITE_POCKETBASE_URL);

  onMount(async () => {
    const articleOne = await pb.collection("articles").getOne(id);
    entry = articleOne;
  })
</script>

<MainMenu/>
<h1>{entry.title}</h1>

<div>
    {@html entry.content}
</div>
<Link to="/articles">⬅️ Back to article list</Link>
