<script>
    import { fly } from "svelte/transition";
    import { cubicOut } from "svelte/easing";
    import { onMount } from "svelte";
  
    let showContent = false;
  
    // Trigger content animation on mount
    onMount(() => {
        showContent = true;
    });
  </script>
  
  <section class="relative w-full flex flex-col md:flex-row items-center md:items-start justify-center md:justify-start overflow-hidden min-h-screen">
    <!-- Background Image (Maintains Aspect Ratio) -->
    <div class="relative w-full md:w-full h-[50vh] md:h-screen sm:h-auto">
        <img 
            src="/icecream.jpg" 
            alt="New Forest Ice Cream" 
            class="w-full h-full object-fit"
        />
    </div>
  
    <!-- Content (Appears with Animation) -->
    {#if showContent}
        <div class="w-full justify-items-center text-blue-900 p-6 md:p-10
                    bg-[#E0F2FE] md:bg-transparent md:absolute md:left-10 md:top-1/2 md:-translate-y-1/2 ">
            
            <p class="text-lg italic font-bold"
                transition:fly="{{ y: 50, opacity: 0, duration: 1200, easing: cubicOut }}">
                SCOOP UP HAPPINESS WITH
            </p>
  
            <h1 class="text-4xl md:text-5xl  font-extrabold  my-4"
                transition:fly="{{ y: 40, opacity: 0, duration: 1400, easing: cubicOut }}">
                New Forest Ice Cream
            </h1>
  
            <p class="text-lg md:text-xl text-blue-900 max-w-2xl mx-auto leading-relaxed font-bold text-center"
                transition:fly="{{ y: 30, opacity: 0, duration: 1600, easing: cubicOut }}">
                We’ve been whipping up smiles since 1983 with our award-winning, nut-free ice cream, sorbets, and desserts.
                Both real dairy ice cream and plant-based treats, and everything in between. Because we’re making the world a cooler place.
            </p>
  
            <!-- CTA Buttons -->
            <div class="mt-6 flex sm:flex-row justify-center gap-4">
                <button class="bg-blue-700 text-white px-6 py-3 rounded-full font-semibold hover:bg-blue-900 transition"
                        transition:fly="{{ y: 20, opacity: 0, duration: 1800, easing: cubicOut }}">
                    Our products
                </button>
                <button class="bg-blue-700 text-white px-6 py-3 rounded-full font-semibold hover:bg-blue-900 transition"
                        transition:fly="{{ y: 15, opacity: 0, duration: 2000, easing: cubicOut }}">
                    Become a customer
                </button>
            </div>
        </div>
    {/if}
  </section>
  