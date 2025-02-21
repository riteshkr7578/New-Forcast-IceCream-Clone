<script>
// @ts-nocheck

    import { fly } from "svelte/transition";
    import { cubicOut } from "svelte/easing";
    import { onMount } from "svelte";

    let showPartner = false;
    let showProducts = false;
    let showBrochure = false;

    onMount(() => {
        const observer = new IntersectionObserver(
            (entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        if (entry.target.id === "partner-section") showPartner = true;
                        if (entry.target.id === "products-section") showProducts = true;
                        if (entry.target.id === "brochure-section") showBrochure = true;
                    }
                });
            },
            { threshold: 0.2 } // Adjusts the scroll trigger
        );

        observer.observe(document.getElementById("partner-section"));
        observer.observe(document.getElementById("products-section"));
        observer.observe(document.getElementById("brochure-section"));
    });
</script>

<section class="w-full bg-[#FFF8DC] py-12 px-6 md:px-16">
    <div class="max-w-6xl mx-auto space-y-20">
        
        <!-- Partner Section -->
        <div id="partner-section" class="grid grid-cols-1 md:grid-cols-2 items-center gap-10">
            <!-- Image -->
            {#if showPartner}
                <div class="relative">
                    <img 
                        src="/iceslice.jpg" 
                        alt="Ice Cream Partnership" 
                        class="w-full h-auto rounded-lg shadow-lg"
                        transition:fly={{ y: 50, opacity: 0, duration: 800, easing: cubicOut }}
                    />
                    <img 
                        src="/bee.svg" 
                        alt="Bee Icon" 
                        class="absolute top-[-20px] left-[-20px] w-16"
                    />
                </div>
            {/if}

            <!-- Content -->
            {#if showPartner}
                <div 
                    class="text-blue-900"
                    transition:fly={{ y: 50, opacity: 0, duration: 1000, easing: cubicOut }}
                >
                    <h2 class="text-3xl md:text-4xl font-extrabold mb-4">
                        Partner with us for irresistible frozen delights
                    </h2>
                    <p class="text-lg text-gray-700 leading-relaxed">
                        Cool down your venue and heat up your sales with our premium frozen treats. 
                        From cozy cafes to bustling theatres, we’re supplying top-notch ice cream and sorbets 
                        to businesses across the South.
                        <br /><br />
                        Join our growing network of satisfied stockists and give your customers something to rave about.
                    </p>
                    <div class="mt-6">
                        <button class="bg-blue-900 text-white px-6 py-3 rounded-full font-semibold hover:bg-blue-800 transition">
                            Trade partners
                        </button>
                    </div>
                </div>
            {/if}
        </div>

        <!-- Products Section -->
        <div id="products-section" class="grid grid-cols-1 md:grid-cols-2 items-center gap-10">
            <!-- Content -->
            {#if showProducts}
                <div 
                    class="text-blue-900 order-2 md:order-1"
                    transition:fly={{ y: 100, opacity: 0, duration: 1000, easing: cubicOut }}
                >
                    <h2 class="text-3xl md:text-4xl font-extrabold mb-4">
                        Browse our products
                    </h2>
                    <p class="text-lg text-gray-700 leading-relaxed">
                        Discover our award-winning ice cream and sorbet range, crafted to elevate your menu 
                        and delight your guests. From classic favourites to innovative flavours, our frozen treats 
                        are made with premium ingredients and perfected recipes.
                    </p>
                    <div class="mt-6">
                        <button class="bg-blue-900 text-white px-6 py-3 rounded-full font-semibold hover:bg-blue-800 transition">
                            Our products
                        </button>
                    </div>
                </div>
            {/if}

            <!-- Image -->
            {#if showProducts}
                <div class="relative order-1 md:order-2">
                    <img 
                        src="/slice2.jpg" 
                        alt="Ice Cream Dessert" 
                        class="w-full h-auto rounded-lg shadow-lg"
                        transition:fly={{ y: 100, opacity: 0, duration: 800, easing: cubicOut }}
                    />
                    <img 
                        src="/leaf.svg" 
                        alt="Leaf Icon" 
                        class="absolute top-[-20px] left-[-20px] w-16"
                    />
                </div>
            {/if}
        </div>

        <!-- Brochure Request Section -->
        <div id="brochure-section" class="flex justify-center">
            {#if showBrochure}
                <div 
                    class="bg-blue-100 px-8 py-10 rounded-4xl shadow-lg text-center w-full md:w-3/4 relative"
                    transition:fly={{ y: 100, opacity: 0, duration: 1000, easing: cubicOut }}
                >
                    <img 
                        src="/bee2.svg" 
                        alt="Butterfly Icon" 
                        class="absolute top-[-20px] left-[-20px] w-16"
                    />
                    <h2 class="text-2xl md:text-3xl font-extrabold text-blue-900">
                        Request a brochure from us today
                    </h2>
                    <p class="text-lg text-gray-700 mt-3">
                        Our brochure gives the complete rundown of our flavours, equipment, and products. Sign up today.
                    </p>
                    <button class="mt-6 bg-blue-900 text-white px-6 py-3 rounded-full font-semibold hover:bg-blue-800 transition">
                        Brochure request
                    </button>
                </div>
            {/if}
        </div>

    </div>
</section>
