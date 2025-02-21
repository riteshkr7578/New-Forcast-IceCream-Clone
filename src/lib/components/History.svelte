<script>
    import { fly } from "svelte/transition";
    import { cubicOut } from "svelte/easing";
    import { onMount } from "svelte";

    let showContent = false;

    onMount(() => {
        const observer = new IntersectionObserver(
            (entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        showContent = true;
                    }
                });
            },
            { threshold: 0.2 } // Adjusts when the content should appear
        );

        // @ts-ignore
        observer.observe(document.getElementById("history-content"));
    });
</script>

<section class="relative w-full flex flex-col md:flex-row items-center md:items-start justify-center md:justify-start overflow-hidden min-h-screen">
    
    <!-- Background Image -->
    <div class="relative w-full md:w-full h-[50vh] md:h-screen">
        <img 
            src="/oldimg.jpg" 
            alt="New Forest History" 
            class="w-full h-full object-fill"
        />
    </div>

    <!-- Content Section -->
    <div id="history-content">
        {#if showContent}
            <div 
                class="w-full md:w-1/2 text-left text-blue-900 p-6 md:p-10
                    bg-[#E0F2FE] md:bg-transparent md:absolute md:left-10 md:top-1/2 md:-translate-y-1/2"
                transition:fly={{ y: 100, opacity: 0, duration: 800, easing: cubicOut }}
            >
                <p class="text-lg italic font-bold">A SCOOP OF HISTORY</p>
                <h2 class="text-3xl md:text-5xl font-extrabold my-4 leading-tight">
                    Dive into our family’s story
                </h2>
                <p class="text-lg md:text-xl text-gray-900">
                    Curious about our New Forest roots?
                </p>

                <!-- Button -->
                <div class="mt-6">
                    <button class="bg-blue-900 text-white px-6 py-3 rounded-full font-semibold hover:bg-blue-800 transition">
                        Our history
                    </button>
                </div>
            </div>
        {/if}
    </div>

</section>
