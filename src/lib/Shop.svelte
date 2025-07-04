<script>
  import ProductCard from './ProductCard.svelte';
  import { products } from '../data.js';
</script>

<div class="px-4 md:px-6 lg:px-40 flex flex-1 justify-center py-5 dark:bg-gray-900">
  <div class="flex flex-col w-full max-w-[960px] flex-1">
    <div class="grid grid-cols-[repeat(auto-fit,minmax(158px,1fr))] gap-3 p-4">
      {#each products as product}
        <ProductCard {product} />
      {/each}
    </div>
  </div>
</div>