<script>
  import { Router, Route } from "svelte-routing";
  import Header from './lib/Header.svelte';
  import Shop from './lib/Shop.svelte';
  import ProductDetail from './lib/ProductDetail.svelte';
  import { onMount } from "svelte";

  onMount(() => {
    if (localStorage.getItem('theme') === 'dark' || (!('theme' in localStorage) && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
      document.documentElement.classList.add('dark')
    } else {
      document.documentElement.classList.remove('dark')
    }
  });
</script>

<Router>
  <div class="flex flex-col min-h-screen bg-white dark:bg-gray-900">
    <Header />
    <main class="flex-grow">
      <Route path="/" component={Shop} />
      <Route path="/product/:id" let:params>
        <ProductDetail id={params.id} />
      </Route>
    </main>
  </div>
</Router>
