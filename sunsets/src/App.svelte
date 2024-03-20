<script>
  import Home from './routes/Home.svelte';
  import Sunset from './routes/Sunset.svelte';
  import { Router, Route } from 'svelte-routing';
</script>

<Router>
  <Route path="/" component={Home}/>
  <Route path="/sunset" component={Sunset}/>
</Router>
