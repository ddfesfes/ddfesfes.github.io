<script>
  import Home from './Component/Home/Home.svelte';
  import portfolio from './Component/portfolio/portfolio.svelte';
  import Router from 'svelte-spa-router';
  //path와 라우팅 할 컴포넌트
  const routes = {
    '/': Home,
    '/pf': portfolio,
    // '/Contact1': Contact,
    // '/Contact2/:test': Contact,
  };
</script>

<main>
  <Router {routes} />
</main>