<script>
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();

  function closeModal() {
    dispatch('close');
  }
</script>

<div class="fixed inset-0 bg-black bg-opacity-50 z-50 flex justify-center items-center" on:click={closeModal}>
  <div class="bg-white dark:bg-gray-800 p-4 rounded-lg max-w-4xl w-full" on:click|stopPropagation>
    <slot></slot>
  </div>
</div>
