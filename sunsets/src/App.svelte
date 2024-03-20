<script>
  import Home from './routes/Home.svelte';
  import Sunset from './routes/Sunset.svelte';
  import { Router, Route } from 'svelte-routing';

  export let url = "";
</script>

<Router {url}>
  <Route path="/" component={Home}/>
  <Route path="/sunset" component={Sunset}/>
</Router>
