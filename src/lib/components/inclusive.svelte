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
                    observer.disconnect(); // Stop observing after appearing once
                }
            },
            { threshold: 0.3 } // Triggers when 30% of the section is visible
        );

        if (sectionRef) {
            observer.observe(sectionRef);
        }
    });
</script>

<section class="relative w-full bg-[#E0F2FE] overflow-hidden" bind:this={sectionRef}>

    <div class="container mx-auto flex flex-col md:flex-row items-center gap-10 py-16 px-6 md:px-16">
        
        <!-- Image (Now flies in) -->
        {#if showContent}
            <div 
                class="w-full md:w-1/2 flex justify-center" 
                transition:fly={{ y: 50, opacity: 0, duration: 1200, easing: cubicOut }}
            >
                <img 
                    src="/children.jpg" 
                    alt="Kids enjoying ice cream" 
                    class="rounded-3xl w-full max-w-md md:max-w-lg shadow-lg object-cover"
                />
            </div>
        {/if}

        <!-- Content (Now flies in) -->
        {#if showContent}
            <div 
                class="w-full md:w-1/2 text-left text-blue-900" 
                transition:fly={{ y: 50, opacity: 0, duration: 1200, easing: cubicOut }}
            >
                <h2 class="text-3xl md:text-5xl font-extrabold mb-4 leading-tight">
                    We’re all about inclusive indulgence
                </h2>
                <p class="text-lg md:text-xl text-gray-900 mb-6">
                    We make our entire range nut-free (except our pistachio, which we make in Italy) 
                    so everyone can chill out and enjoy. Additionally, we’ve churned up some seriously 
                    creamy plant-based options. Listen up, Scoop Troop – there’s absolutely no compromise 
                    on flavour here!
                </p>

                <!-- Button -->
                <button class="bg-blue-900 text-white px-6 py-3 rounded-full font-semibold hover:bg-blue-800 transition">
                    Dietary & allergens
                </button>
            </div>
        {/if}

    </div>
</section>
