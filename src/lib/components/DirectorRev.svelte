<script>
    import { fly } from "svelte/transition";
    import { cubicOut } from "svelte/easing";
    import { onMount, onDestroy } from "svelte";
    import { browser } from "$app/environment"; // ✅ Check if it's running in the browser

    let showContent = false;

    function handleScroll() {
        if (!browser) return; // Prevents running on the server

        const section = document.getElementById("testimonial-section");
        if (section) {
            const rect = section.getBoundingClientRect();
            if (rect.top < window.innerHeight * 0.8) {
                showContent = true;
                window.removeEventListener("scroll", handleScroll);
            }
        }
    }

    onMount(() => {
        if (browser) {
            window.addEventListener("scroll", handleScroll);
            handleScroll(); // Check visibility on mount
        }
    });

    onDestroy(() => {
        if (browser) {
            window.removeEventListener("scroll", handleScroll);
        }
    });
</script>

<section 
    id="testimonial-section"
    class="relative bg-[#FFEB99] inset-0 py-16 px-6 md:px-16 w-full border-1"
>
    <div class="max-w-7xl mx-auto grid grid-cols-1 md:grid-cols-2 items-center gap-10 relative z-10">
        
        <!-- Image Section -->
        {#if showContent}
            <div class="flex justify-center">
                <img 
                    src="/slice3.jpg" 
                    alt="Testimonial Ice Cream" 
                    class="w-full max-w-lg rounded-lg shadow-lg"
                    transition:fly={{ y: 100, opacity: 0, duration: 800, easing: cubicOut }}
                />
            </div>
        {/if}

        <!-- Text Content -->
        {#if showContent}
            <div 
                class="text-blue-900 text-center md:text-left px-4"
                transition:fly={{ y: 100, opacity: 0, duration: 1000, easing: cubicOut }}
            >
                <h2 class="text-3xl md:text-4xl font-extrabold mb-4 flex justify-center md:justify-start items-center gap-2">
                    <span class="text-yellow-500 text-5xl">“</span> 
                    Paultons Park is proud
                </h2>
                <p class="text-lg text-gray-700 leading-relaxed">
                    Paultons Park is proud to have a long-standing relationship 
                    with New Forest Ice Cream that goes back many years. 
                    Indeed, to source from a local company a first-class, quality 
                    product which is supplied in a reliable and efficient manner 
                    is a real bonus. Moreover, New Forest Ice Cream supplies 
                    all our ice cream requirements today, and consequently, 
                    we very much value their first-class service.
                </p>
                <p class="mt-4 font-bold italic text-blue-900">
                    Stephen Lorton – Commercial Director
                </p>
            </div>
        {/if}

    </div>
</section>
