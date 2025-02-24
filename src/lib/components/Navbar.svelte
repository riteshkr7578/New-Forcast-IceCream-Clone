<script>
    import { writable } from "svelte/store";
   
    let isOpen = writable(false);
  
    function toggleMenu() {
      isOpen.update(n => !n);
    }
  </script>
  
  <header class=" top-0 w-full z-50 bg-white shadow-md">
    <!-- Top Blue Bar -->
    <div class="bg-blue-900 text-white text-sm text-center py-2">
      Already got a trade account? 
      <a href="#" class="underline font-semibold">Order online</a>
    </div>
  
    <!-- Navbar -->
    <nav class="container mx-auto flex items-center justify-between py-4 px-6 md:px-12">
      <!-- Left Links -->
      <ul class="hidden md:flex space-x-16 text-blue-900 font-bold">
        <li><a href="/products" class="hover:text-blue-700 transition text-2xl">Products</a></li>
        <li><a href="/trade" class="hover:text-blue-700 transition text-2xl">Trade</a></li>
        <li><a href="/about" class="hover:text-blue-700 transition text-2xl">About</a></li>
      </ul>
  
      <!-- Logo (Centered) -->
      <a href="/" class="w-32 ml-8">
        <img src="/logo.svg" alt="New Forest Ice Cream" class="w-full">
      </a>
  
      <!-- Right Links -->
      <ul class="hidden md:flex space-x-16 text-blue-900 font-bold">
        <li><a href="/blog" class="hover:text-blue-700 transition text-2xl">The Scoop Blog</a></li>
        <li><a href="/mission-green" class="hover:text-blue-700 transition text-2xl">Mission Green</a></li>
        <li><a href="/contact" class="hover:text-blue-700 transition text-2xl">Contact</a></li>
      </ul>
  
      <!-- Mobile Menu Button -->
      <button class="md:hidden text-3xl" on:click={toggleMenu}>
        ☰
      </button>
    </nav>
  
    <!-- Mobile Menu -->
    {#if $isOpen}
    <div class="md:hidden bg-white shadow-lg p-4">
      <ul class="flex flex-col space-y-4 text-center font-bold text-blue-900">
        <li><a href="/products">Products</a></li>
        <li><a href="/trade">Trade</a></li>
        <li><a href="/about">About</a></li>
        <li><a href="/blog">The Scoop Blog</a></li>
        <li><a href="/mission-green">Mission Green</a></li>
        <li><a href="/contact">Contact</a></li>
      </ul>
    </div>
    {/if}
  </header>
  
