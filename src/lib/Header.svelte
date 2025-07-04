<script>
  import { Link } from "svelte-routing";
  import ThemeSwitcher from "./ThemeSwitcher.svelte";

  let isMenuOpen = false;

  function toggleMenu() {
    isMenuOpen = !isMenuOpen;
  }
</script>

<header class="flex items-center justify-between whitespace-nowrap border-b border-solid border-b-[#f2f2f2] px-4 sm:px-10 py-3 dark:bg-gray-800 dark:border-gray-700">
  <div class="flex items-center gap-4 text-[#141414] dark:text-white">
    <div class="size-4">
      <svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path
          d="M36.7273 44C33.9891 44 31.6043 39.8386 30.3636 33.69C29.123 39.8386 26.7382 44 24 44C21.2618 44 18.877 39.8386 17.6364 33.69C16.3957 39.8386 14.0109 44 11.2727 44C7.25611 44 4 35.0457 4 24C4 12.9543 7.25611 4 11.2727 4C14.0109 4 16.3957 8.16144 17.6364 14.31C18.877 8.16144 21.2618 4 24 4C26.7382 4 29.123 8.16144 30.3636 14.31C31.6043 8.16144 33.9891 4 36.7273 4C40.7439 4 44 12.9543 44 24C44 35.0457 40.7439 44 36.7273 44Z"
          fill="currentColor"
        ></path>
      </svg>
    </div>
    <h2 class="text-[#141414] text-lg font-bold leading-tight tracking-[-0.015em] dark:text-white">Zenith</h2>
  </div>

  <!-- Hamburger Menu Button -->
  <div class="sm:hidden">
    <button on:click={toggleMenu} class="text-[#141414] dark:text-white">
      <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7"></path>
      </svg>
    </button>
  </div>

  <!-- Desktop Menu -->
  <div class="hidden sm:flex flex-1 justify-end gap-8">
    <div class="flex items-center gap-9">
      <Link to="/" class="text-[#141414] text-sm font-medium leading-normal dark:text-white">Shop</Link>
      <a class="text-[#141414] text-sm font-medium leading-normal dark:text-white" href="#">About</a>
      <a class="text-[#141414] text-sm font-medium leading-normal dark:text-white" href="#">Contact</a>
    </div>
    <div class="flex gap-2">
      <button
        class="flex max-w-[480px] cursor-pointer items-center justify-center overflow-hidden rounded-lg h-10 bg-[#f2f2f2] text-[#141414] gap-2 text-sm font-bold leading-normal tracking-[0.015em] min-w-0 px-2.5 dark:bg-gray-700 dark:text-white"
      >
        <div class="text-[#141414] dark:text-white" data-icon="MagnifyingGlass" data-size="20px" data-weight="regular">
          <svg xmlns="http://www.w3.org/2000/svg" width="20px" height="20px" fill="currentColor" viewBox="0 0 256 256">
            <path
              d="M229.66,218.34l-50.07-50.06a88.11,88.11,0,1,0-11.31,11.31l50.06,50.07a8,8,0,0,0,11.32-11.32ZM40,112a72,72,0,1,1,72,72A72.08,72.08,0,0,1,40,112Z"
            ></path>
          </svg>
        </div>
      </button>
      <button
        class="flex max-w-[480px] cursor-pointer items-center justify-center overflow-hidden rounded-lg h-10 bg-[#f2f2f2] text-[#141414] gap-2 text-sm font-bold leading-normal tracking-[0.015em] min-w-0 px-2.5 dark:bg-gray-700 dark:text-white"
      >
        <div class="text-[#141414] dark:text-white" data-icon="ShoppingBag" data-size="20px" data-weight="regular">
          <svg xmlns="http://www.w3.org/2000/svg" width="20px" height="20px" fill="currentColor" viewBox="0 0 256 256">
            <path
              d="M216,40H40A16,16,0,0,0,24,56V200a16,16,0,0,0,16,16H216a16,16,0,0,0,16-16V56A16,16,0,0,0,216,40Zm0,160H40V56H216V200ZM176,88a48,48,0,0,1-96,0,8,8,0,0,1,16,0,32,32,0,0,0,64,0,8,8,0,0,1,16,0Z"
            ></path>
          </svg>
        </div>
      </button>
      <ThemeSwitcher />
    </div>
  </div>

  <!-- Mobile Menu -->
  {#if isMenuOpen}
    <div class="sm:hidden absolute top-16 left-0 w-full bg-white dark:bg-gray-800 z-10">
      <div class="flex flex-col items-center gap-4 py-4">
        <Link to="/" class="text-[#141414] text-sm font-medium leading-normal dark:text-white">Shop</Link>
        <a class="text-[#141414] text-sm font-medium leading-normal dark:text-white" href="#">About</a>
        <a class="text-[#141414] text-sm font-medium leading-normal dark:text-white" href="#">Contact</a>
        <div class="flex gap-2 mt-4">
          <button
            class="flex max-w-[480px] cursor-pointer items-center justify-center overflow-hidden rounded-lg h-10 bg-[#f2f2f2] text-[#141414] gap-2 text-sm font-bold leading-normal tracking-[0.015em] min-w-0 px-2.5 dark:bg-gray-700 dark:text-white"
          >
            <div class="text-[#141414] dark:text-white" data-icon="MagnifyingGlass" data-size="20px" data-weight="regular">
              <svg xmlns="http://www.w3.org/2000/svg" width="20px" height="20px" fill="currentColor" viewBox="0 0 256 256">
                <path
                  d="M229.66,218.34l-50.07-50.06a88.11,88.11,0,1,0-11.31,11.31l50.06,50.07a8,8,0,0,0,11.32-11.32ZM40,112a72,72,0,1,1,72,72A72.08,72.08,0,0,1,40,112Z"
                ></path>
              </svg>
            </div>
          </button>
          <button
            class="flex max-w-[480px] cursor-pointer items-center justify-center overflow-hidden rounded-lg h-10 bg-[#f2f2f2] text-[#141414] gap-2 text-sm font-bold leading-normal tracking-[0.015em] min-w-0 px-2.5 dark:bg-gray-700 dark:text-white"
          >
            <div class="text-[#141414] dark:text-white" data-icon="ShoppingBag" data-size="20px" data-weight="regular">
              <svg xmlns="http://www.w3.org/2000/svg" width="20px" height="20px" fill="currentColor" viewBox="0 0 256 256">
                <path
                  d="M216,40H40A16,16,0,0,0,24,56V200a16,16,0,0,0,16,16H216a16,16,0,0,0,16-16V56A16,16,0,0,0,216,40Zm0,160H40V56H216V200ZM176,88a48,48,0,0,1-96,0,8,8,0,0,1,16,0,32,32,0,0,0,64,0,8,8,0,0,1,16,0Z"
                ></path>
              </svg>
            </div>
          </button>
          <ThemeSwitcher />
        </div>
      </div>
    </div>
  {/if}
</header>
