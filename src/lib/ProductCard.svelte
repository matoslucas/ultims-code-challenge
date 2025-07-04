<script>
  import { Link } from "svelte-routing";
  export let product;
</script>

<div class="flex flex-col gap-3 pb-3 w-full">
  <Link to={`/product/${product.id}`}>
    <div
      class="w-full bg-center bg-no-repeat aspect-[3/4] bg-cover rounded-lg"
      style="background-image: url({product.image});"
    ></div>
    <div>
      <p class="text-[#141414] text-base font-medium leading-normal dark:text-white">{product.name}</p>
      <p class="text-[#757575] text-sm font-normal leading-normal dark:text-gray-400">${product.price}</p>
    </div>
  </Link>
</div>