<script>
  import {Link} from 'svelte5-router';
  import {onMount} from 'svelte';
  import PocketBase from "pocketbase";

  let entries = $state([]);
  const pb = new PocketBase(import.meta.env.VITE_POCKETBASE_URL);

  onMount(async () => {
    const articleList = await pb.collection("articles").getList();
    entries = articleList.items;
  })
</script>

<h1 class="uk-h1">Articles</h1>

<div>
  {#each entries as item}
  <div class="uk-card uk-card-body space-y-6 mb-4">
    <Link to="/articles/{item.id}" class="">
      <div class="flex gap-x-4">
        <div class="flex-1">
          <h3 class="uk-h3">
            {item.title}
          </h3>
          <p class="mt-2 text-muted-foreground">
            {item.updated}
          </p>
        </div>
      </div>
    </Link>
  </div>
  {/each}
</div>
