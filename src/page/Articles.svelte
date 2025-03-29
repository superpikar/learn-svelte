<script>
  import { Link } from 'svelte5-router';
  import { onMount } from 'svelte';
  import MainMenu from "../lib/MainMenu.svelte";
  import PocketBase from "pocketbase";

  let entries = $state([]);
  const pb = new PocketBase(import.meta.env.VITE_POCKETBASE_URL);

  onMount(async () => {
    const articleList = await pb.collection("articles").getList();
    entries = articleList.items;
  })
</script>

<MainMenu/>
<h1>Articles</h1>

<ul>
{#each entries as item}
    <li>
        <Link to="/articles/{item.id}">{item.title}</Link>
    </li>
{/each}
</ul>
