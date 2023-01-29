<script>
  import { Route, Router } from "svelte-routing";
  import BottomBar from "./components/BottomBar.svelte";
  import BestStories from "./views/BestStories.svelte";

  import Index from "./views/Index.svelte";
  import TopStories from "./views/TopStories.svelte";

  export let url = "";
</script>

<Router {url}>
  <div>
    <Route path="/" component={Index} />
    <Route path="/topstories" component={TopStories} />
    <Route path="/beststories" component={BestStories} />
  </div>
  <BottomBar />
</Router>
