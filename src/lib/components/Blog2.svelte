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
            { threshold: 0.3 } // Trigger when 30% of the section is visible
        );

        if (sectionRef) {
            observer.observe(sectionRef);
        }
    });
</script>

<div class="bg-[#FEFCE8] flex justify-center py-10 px-4" bind:this={sectionRef}>
    {#if showContent}
        <div 
            class="grid grid-cols-1 md:grid-cols-2 gap-4 max-w-6xl w-full relative"
            transition:fly={{ y: 50, opacity: 0, duration: 1200, easing: cubicOut }}
        >
            <!-- Big Vegan Ice Cream Block -->
            <div class="relative col-span-2 md:col-span-1 rounded-3xl shadow-lg">
                <img src="/ice1.jpg" alt="Vegan Ice Cream" class="w-full h-full object-fill">
                <img 
                    src="/leaf.svg" 
                    alt="Leaf Icon" 
                    class="absolute top-[-20px] left-[-20px] w-16"
                />
                <div class="absolute inset-0 bg-opacity-30 flex flex-col justify-end p-6">
                    <h1 class="text-white text-2xl md:text-5xl font-bold leading-tight">
                        Delight in dairy-free: Exploring the best of plant-based vegan ice creams this Veganuary.
                    </h1>
                </div>
            </div>

            <!-- Dairy Turkish Delight -->
            <div 
                class="relative overflow-hidden"
                transition:fly={{ y: 50, opacity: 0, duration: 1300, easing: cubicOut }}
            >
                <img src="/ice2.jpg" alt="Dairy Turkish Delight" class="w-full h-70 object-cover rounded-3xl">
                <div class="absolute inset-0 bg-opacity-30 flex justify-start mt-50 ml-5">
                    <h1 class="text-white text-lg md:text-3xl font-bold">Dairy Turkish Delight</h1>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-2 space-x-4 h-80">
                    <!-- Valentine's Day -->
                    <div 
                        class="relative rounded-3xl overflow-hidden shadow-lg bg-gradient-to-b from-[#FDE2E4] to-[#FAD2E1] flex justify-start mt-5 bg-cover bg-center items-end"
                        style="background-image: url('/ice3.jpg');"
                        transition:fly={{ y: 50, opacity: 0, duration: 1400, easing: cubicOut }}
                    >
                        <h1 class="text-white text-lg md:text-3xl font-bold mb-10 ml-3">Valentine’s Day</h1>
                    </div>

                    <!-- Blog Section -->
                    <div 
                        class="relative rounded-3xl overflow-hidden shadow-lg bg-[#FFC1C1] flex flex-col items-center justify-center p-6 text-center mt-5 hover:bg-[#EE6688]"
                        transition:fly={{ y: 50, opacity: 0, duration: 1500, easing: cubicOut }}
                    >
                        <p class="text-[#dd5454] font-semibold">Our Blog</p>
                        <h1 class="text-[#a42727] text-lg md:text-xl font-bold">Scoop yourself some sweet updates</h1>
                        <!-- svelte-ignore a11y_invalid_attribute -->
                        <a href="#" class="mt-3 inline-block px-4 py-2 bg-white text-black rounded-full font-semibold">Discover more</a>
                    </div>
                </div>
            </div>
        </div>
    {/if}
</div>
