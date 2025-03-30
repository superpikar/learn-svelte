<script>
  import { Router, Route } from "svelte5-router";
  import Welcome from "./page/Welcome.svelte";
  import About from "./page/About.svelte";
  import Articles from "./page/Articles.svelte";
  import Article from "./page/Article.svelte";
  import MainMenu from "./lib/MainMenu.svelte";

  let url = "";
</script>

<!-- START CODING HERE -->
<Router {url}>
  <div class="uk-container">
    <MainMenu url="{url}" />
    <div class="space-y-4 mt-10">
      <!-- any component should inside Router!! -->
      <Route path="/about" component={About} />
      <Route path="/articles" component={Articles} />
      <Route path="/articles/:id">
        {#snippet children(params)}
          <Article id="{params.id}"  />
        {/snippet}
      </Route>
      <Route path="/">
        <Welcome/>
      </Route>
    </div>
  </div>
</Router>
<!-- END -->