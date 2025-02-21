<script>
    import { fly } from "svelte/transition";
    import { cubicOut } from "svelte/easing";
    import { onMount } from "svelte";

    let showContent = false;
    let sectionRef;

    onMount(() => {
        const observer = new IntersectionObserver(
            ([entry]) => {
                if (entry.isIntersecting) {
                    showContent = true;
                    observer.disconnect(); // Stop observing after first trigger
                }
            },
            { threshold: 0.3 } // Trigger when 30% visible
        );

        if (sectionRef) {
            observer.observe(sectionRef);
        }
    });
</script>

<section class="relative w-full bg-[#FEFCE8] pb-20 overflow-hidden" bind:this={sectionRef}>
    <!-- Top Wave -->

    <div class="container mx-auto px-6 md:px-16 mt-10">
        <!-- Sustainability Section -->
        {#if showContent}
            <div 
                class="relative bg-[#B7E5A1] rounded-xl p-6 md:p-10 shadow-lg max-w-4xl mx-auto mb-12"
                transition:fly={{ y: 50, opacity: 0, duration: 1200, easing: cubicOut }}
            >
                <!-- Bee Image (Positioned at the Top-Left, Slightly Outside) -->
                <img src="/bee.svg" alt="Bee" 
                    class="absolute -top-6 -left-6 w-12 md:w-16" />
        
                <p class="text-sm md:text-base italic font-semibold text-[#2D4A22]">SUSTAINABILITY</p>
                <h2 class="text-xl md:text-2xl font-bold text-[#002F6C]">
                    Check out our eco-friendly initiatives
                </h2>
                <p class="text-[#002F6C] mt-2">
                    We commit to a greener future through both our sourcing and packaging. So learn more about our impact.
                </p>
                <button class="mt-4 px-6 py-2 bg-[#002F6C] text-white rounded-full shadow-md hover:bg-[#001E4C]">
                    Mission Green
                </button>
            </div>
        {/if}
    </div>
</section>
