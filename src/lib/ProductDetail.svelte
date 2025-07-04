<script>
  import { products } from '../data.js';
  import Modal from './Modal.svelte';
  import Carousel from './Carousel.svelte';

  export let id;

  $: product = products.find(p => p.id === parseInt(id));

  let showModal = false;
  let currentImageIndex = 0;
  let selectedColor = '';
  let selectedSize = '';

  // Set default selected color and size when product is loaded
  $: if (product) {
    selectedColor = product.colors && product.colors.length > 0 ? product.colors[0] : '';
    selectedSize = product.sizes && product.sizes.length > 0 ? product.sizes[0] : '';
  }

  function openModal(index) {
    currentImageIndex = index;
    showModal = true;
  }

  function closeModal() {
    showModal = false;
  }
</script>

{#if product}
<div class="flex flex-col md:flex-row gap-4 px-4 md:px-6 lg:px-40 py-5 dark:bg-gray-900">
  <!-- Image Section -->
  <div class="flex flex-col w-full md:w-2/5">

    <!-- Desktop Main Image + Thumbnails (hidden on mobile) -->
    <div class="hidden md:block">
      <!-- Main Product Image -->
      <div class="w-full aspect-[2/3] rounded-xl overflow-hidden cursor-pointer mb-4"
           style="background-image: url({product.images[0]}); background-size: cover; background-position: center;"
           on:click={() => openModal(0)}>
      </div>

      <!-- Desktop Thumbnail Grid -->
      <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 gap-2">
        {#each product.images.slice(1) as image, i}
          <div class="w-full aspect-[2/3] rounded-xl overflow-hidden cursor-pointer"
               style="background-image: url({image}); background-size: cover; background-position: center;"
               on:click={() => openModal(i + 1)}>
          </div>
        {/each}
      </div>
    </div>

    <!-- Mobile All Thumbnails (hidden on desktop) -->
    <div class="md:hidden">
      <div class="grid grid-cols-2 sm:grid-cols-3 gap-2">
        {#each product.images as image, i}
          <div class="w-full aspect-[2/3] rounded-xl overflow-hidden cursor-pointer max-h-24"
               style="background-image: url({image}); background-size: cover; background-position: center;"
               on:click={() => openModal(i)}>
          </div>
        {/each}
      </div>
    </div>

  </div>

  <!-- Product Details Section -->
  <div class="flex flex-col w-full md:flex-1 md:max-w-[960px]">
    <h2 class="text-[#111418] tracking-light text-[28px] font-bold leading-tight px-4 text-left pb-3 pt-5 dark:text-white">{product.name}</h2>
    <p class="text-[#60728a] text-sm font-normal leading-normal pb-3 pt-1 px-4 dark:text-gray-400">${product.price}</p>
    <p class="text-[#111418] text-base font-normal leading-normal pb-3 pt-1 px-4 dark:text-white md:hidden">
      {product.shortDescription}
    </p>
    <p class="text-[#111418] text-base font-normal leading-normal pb-3 pt-1 px-4 dark:text-white hidden md:block">
      {product.description}
    </p>

    <!-- Color Options -->
    {#if product.colors && product.colors.length > 0}
      <div class="px-4 py-3">
        <h3 class="text-[#111418] text-base font-bold leading-normal mb-2 dark:text-white">Color:</h3>
        <div class="flex flex-wrap gap-2">
          {#each product.colors as color}
            <label class="inline-flex items-center">
              <input
                type="radio"
                name="color"
                value={color}
                bind:group={selectedColor}
                class="form-radio h-4 w-4 text-[#3889f4] border-gray-300 focus:ring-[#3889f4] dark:border-gray-600 dark:bg-gray-700 dark:checked:bg-[#3889f4]"
              />
              <span class="ml-2 text-[#111418] dark:text-white">{color}</span>
            </label>
          {/each}
        </div>
      </div>
    {/if}

    <!-- Size Options -->
    {#if product.sizes && product.sizes.length > 0}
      <div class="px-4 py-3">
        <h3 class="text-[#111418] text-base font-bold leading-normal mb-2 dark:text-white">Size:</h3>
        <select
          bind:value={selectedSize}
          class="block w-full max-w-xs px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-[#3889f4] focus:border-[#3889f4] sm:text-sm dark:bg-gray-700 dark:border-gray-600 dark:text-white"
        >
          {#each product.sizes as size}
            <option value={size}>{size}</option>
          {/each}
        </select>
      </div>
    {/if}

    <div class="flex px-4 py-3 justify-start">
      <button
        class="flex min-w-[84px] max-w-[480px] cursor-pointer items-center justify-center overflow-hidden rounded-xl h-12 px-5 bg-[#3889f4] text-white text-base font-bold leading-normal tracking-[0.015em]"
      >
        <span class="truncate">Add to Cart</span>
      </button>
    </div>
  </div>
</div>
{:else}
  <p class="text-center text-lg">Loading product...</p>
{/if}

{#if showModal}
  <Modal on:close={closeModal}>
    <Carousel images={product.images} initialIndex={currentImageIndex} />
  </Modal>
{/if}
