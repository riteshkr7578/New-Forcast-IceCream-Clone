<script>
    import { onMount, onDestroy } from "svelte";
    import { browser } from "$app/environment"; // Prevent SSR errors

    const logos = [
        { src: "/paultons.webp", alt: "Paultons Park" },
        { src: "/BCP.png", alt: "BCP Council" },
        { src: "/Marwell.webp", alt: "Marwell Wildlife" },
        { src: "/hoburne.webp", alt: "Hoburne Holidays" },
        { src: "/southern.webp", alt: "Southern Coop" },
        { src: "/country.webp", alt: "Country Fare" },
        { src: "/premier.webp", alt: "Premier Foods" },
        { src: "/harvest.webp", alt: "Harvest Fine Foods" },
        { src: "/hopwells.webp", alt: "Hopwells" },
        { src: "/more.webp", alt: "And More" }
    ];

    let showLogos = false;

    function handleScroll() {
        if (!browser) return; // Ensure this runs only in the browser

        const section = document.getElementById("logo-section");
        if (section) {
            const rect = section.getBoundingClientRect();
            if (rect.top < window.innerHeight * 0.85) { // Trigger when 85% visible
                showLogos = true;
                window.removeEventListener("scroll", handleScroll); // Remove listener once activated
            }
        }
    }

    onMount(() => {
        if (browser) {
            window.addEventListener("scroll", handleScroll);
            handleScroll(); // Check immediately in case already in view
        }
    });

    onDestroy(() => {
        if (browser) {
            window.removeEventListener("scroll", handleScroll);
        }
    });
</script>

<section 
    id="logo-section"
    class="bg-[#FDF6DD] py-16 px-6 md:px-16 text-center"
>
    <h2 class="text-3xl md:text-4xl font-extrabold text-blue-900 mb-6">
        <span class="italic text-lg text-blue-600">Scoop Squad Assemble</span><br />
        Our Cool Collaborators
    </h2>

    <!-- Logo Grid -->
    <div class="max-w-7xl mx-auto grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-x-10 gap-y-8 items-center justify-items-center">
        {#each logos as logo, i}
            <img 
                src={logo.src} 
                alt={logo.alt} 
                class="h-16 md:h-20 lg:h-24 object-contain transition-transform duration-700 ease-out
      {showLogos ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'}"

                style="transition-delay: {i * 100}ms;" 
            />
        {/each}
    </div>
</section>
