<script>
  import { Router, Route } from "svelte5-router";
  import Welcome from "./page/Welcome.svelte";
  import About from "./page/About.svelte";
  import Dashboard from "./page/Dashboard.svelte";

  let url = "";
</script>

<Router {url}>
  <Route path="/about" component={About} />
  <Route path="/dashboard" component={Dashboard} />
  <Route path="/"><Welcome/></Route>
</Router>