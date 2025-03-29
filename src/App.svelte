<script>
  import { Router, Route } from "svelte5-router";
  import Welcome from "./page/Welcome.svelte";
  import About from "./page/About.svelte";
  import Articles from "./page/Articles.svelte";
  import Article from "./page/Article.svelte";

  let url = "";
</script>

<Router {url}>
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
</Router>