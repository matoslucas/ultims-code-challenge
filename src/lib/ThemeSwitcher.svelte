<script>
  import { onMount } from 'svelte';

  let isDarkMode = false;

  onMount(() => {
    isDarkMode = localStorage.getItem('theme') === 'dark';
    updateTheme();
  });

  function toggleTheme() {
    isDarkMode = !isDarkMode;
    localStorage.setItem('theme', isDarkMode ? 'dark' : 'light');
    updateTheme();
  }

  function updateTheme() {
    if (isDarkMode) {
      document.documentElement.classList.add('dark');
    } else {
      document.documentElement.classList.remove('dark');
    }
  }
</script>

<button on:click={toggleTheme} class="flex max-w-[480px] cursor-pointer items-center justify-center overflow-hidden rounded-lg h-10 bg-[#f2f2f2] text-[#141414] gap-2 text-sm font-bold leading-normal tracking-[0.015em] min-w-0 px-2.5 dark:bg-gray-700 dark:text-white">
  {#if isDarkMode}
    <svg xmlns="http://www.w3.org/2000/svg" width="20px" height="20px" fill="currentColor" viewBox="0 0 256 256"><path d="M120,40V16a8,8,0,0,1,16,0V40a8,8,0,0,1-16,0Zm72,88a8,8,0,0,0-8,8v8a40,40,0,0,1-40,40H96a40,40,0,0,1-40-40v-8a8,8,0,0,0-16,0v8a56,56,0,0,0,56,56h32a56,56,0,0,0,56-56v-8A8,8,0,0,0,192,128Zm-32-48a8,8,0,0,0,5.66-2.34l11.31-11.32a8,8,0,0,0-11.31-11.31L154.34,74.34a8,8,0,0,0,5.66,13.66ZM74.34,74.34A8,8,0,0,0,80,60.69L68.69,49.37A8,8,0,0,0,57.37,60.69L68.69,72a8,8,0,0,0,5.65,2.34ZM40,120H16a8,8,0,0,0,0,16H40a8,8,0,0,0,0-16Zm176,0H216a8,8,0,0,0,0,16h24a8,8,0,0,0,0-16Z"></path></svg>
  {:else}
    <svg xmlns="http://www.w3.org/2000/svg" width="20px" height="20px" fill="currentColor" viewBox="0 0 256 256"><path d="M235.54,150.21a104.84,104.84,0,0,1-39.45,39.45,104.2,104.2,0,0,1-141-141,104.84,104.84,0,0,1,39.45-39.45,103.8,103.8,0,0,1,11.31-2.59,8,8,0,0,1,4.2,15.21,79.83,79.83,0,0,0,2,115.18,80.2,80.2,0,0,0,115.18,2,8,8,0,0,1,15.21,4.2A103.8,103.8,0,0,1,235.54,150.21Z"></path></svg>
  {/if}
</button>
