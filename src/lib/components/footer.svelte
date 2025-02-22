<script>
    import { onMount } from "svelte";

    onMount(() => {
        const newsletter = document.querySelector("#newsletter");
        if (!newsletter) return;

        const observer = new IntersectionObserver(
            (entries) => {
                entries.forEach((entry) => {
                    if (entry.isIntersecting) {
                        newsletter.classList.remove("opacity-0", "translate-y-10");
                        newsletter.classList.add("opacity-100", "translate-y-0");
                        observer.unobserve(entry.target);
                    }
                });
            },
            { threshold: 0.2 } // Triggers when 20% is visible
        );

        observer.observe(newsletter);
    });
</script>

<footer class="bg-[#CDEAFF]">
    <div id="newsletter" class="py-16 px-4 opacity-0 translate-y-10 transition-all duration-700">
        <div class="max-w-6xl mx-auto">
            <div class="bg-[#FEFCE8] rounded-3xl p-8 md:p-12 flex flex-col md:flex-row items-center justify-between gap-6">
                <!-- Left Side: Newsletter Heading & Social Icons -->
                <div class="flex flex-col items-start space-y-4">
                    <p class="text-[#003580] font-semibold italic">Newsletter!</p>
                    <h2 class="text-[#003580] text-2xl md:text-3xl font-bold leading-tight">
                        Fancy receiving the latest <br class="hidden md:block">scoop straight to your inbox?
                    </h2>
                    <div class="flex space-x-3">
                        <a href="https://www.instagram.com" aria-label="Instagram">
                            <img src="/instagram.svg" alt="Instagram" class="w-6 h-6">
                        </a>
                        <a href="https://www.facebook.com" aria-label="Facebook">
                            <img src="/facebook.svg" alt="Facebook" class="w-6 h-6">
                        </a>
                        <a href="https://www.linkedin.com" aria-label="LinkedIn">
                            <img src="linkdin.svg" alt="LinkedIn" class="w-6 h-6">
                        </a>
                    </div>
                </div>

                <!-- Right Side: Subscription Form -->
                <div class="flex flex-col items-start space-y-4">
                    <p class="text-[#003580]">Sign up to our newsletter to receive the latest news, updates, and offers from New Forest Ice Cream.</p>
                    <label for="email" class="text-[#003580] font-semibold">Email *</label>
                    <div class="flex flex-col sm:flex-row items-center space-y-3 sm:space-y-0 sm:space-x-2">
                        <input type="email" id="email" placeholder="Your email address" 
                            class="px-4 py-3 rounded-full border border-gray-300 focus:outline-none focus:ring-2 focus:ring-[#003580]">
                        <button class="bg-[#003580] text-white px-6 py-3 rounded-full font-semibold hover:bg-[#001f4d] transition">
                            Subscribe
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>


    <!-- Main Footer Section -->
    <div class="bg-[#CDEAFF] px-6 py-12">
        <div class="max-w-6xl mx-auto grid grid-cols-1 md:grid-cols-5 gap-6 text-[#003580]">
            <!-- Logo -->
            <div class="flex justify-center md:justify-start ">
                <img src="/logo.svg" alt="New Forest Ice Cream" class="w-32 md:w-40">
            </div>
            
            <!-- Our Products -->
            <div>
                <h3 class="font-bold text-lg mb-3">Our products</h3>
                <ul class="space-y-2">
                    <li><a href="#" class="hover:text-[#001f4d]">Scoop</a></li>
                    <li><a href="#" class="hover:text-[#001f4d]">Tubs</a></li>
                    <li><a href="#" class="hover:text-[#001f4d]">New Forest Soft Serve</a></li>
                    <li><a href="#" class="hover:text-[#001f4d]">Impulse range</a></li>
                    <li><a href="#" class="hover:text-[#001f4d]">Cakes & desserts</a></li>
                    <li><a href="#" class="hover:text-[#001f4d]">Other products</a></li>
                    <li><a href="#" class="hover:text-[#001f4d]">Order online</a></li>
                    <li><a href="#" class="hover:text-[#001f4d]">Dietary & allergens</a></li>
                </ul>
            </div>

            <!-- About -->
            <div>
                <h3 class="font-bold text-lg mb-3">About</h3>
                <ul class="space-y-2">
                    <li><a href="#" class="hover:text-[#001f4d]">Trade</a></li>
                    <li><a href="#" class="hover:text-[#001f4d]">About us</a></li>
                    <li><a href="#" class="hover:text-[#001f4d]">Our history</a></li>
                    <li><a href="#" class="hover:text-[#001f4d]">Careers</a></li>
                    <li><a href="#" class="hover:text-[#001f4d]">Our blog</a></li>
                    <li><a href="#" class="hover:text-[#001f4d]">Environment</a></li>
                    <li><a href="#" class="hover:text-[#001f4d]">Recycling</a></li>
                </ul>
            </div>

            <!-- Contact & Follow Us -->
            <div>
                <h3 class="font-bold text-lg mb-3">Contact</h3>
                <p>01590 647 611</p>
                <p><a href="mailto:info@nfic.co.uk" class="hover:text-[#001f4d]">info@nfic.co.uk</a></p>
                <p><a href="mailto:orders@nfic.co.uk" class="hover:text-[#001f4d]">orders@nfic.co.uk</a></p>
                <p>630 Ampress Lane <br> Ampress Park <br> Lymington, Hampshire <br> SO41 8LW</p>
                
                
            </div>

            <!-- Follow Us -->
             <div>
            <h3 class="font-bold text-lg mt-0">Follow us</h3>
            <div class="flex space-x-3 mt-2">
                <a href="https://www.instagram.com" aria-label="Instagram">
                    <img src="/instagram.svg" alt="Instagram" class="w-6 h-6">
                </a>
                <a href="https://www.facebook.com" aria-label="Facebook">
                    <img src="/facebook.svg" alt="Facebook" class="w-6 h-6">
                </a>
                <a href="https://www.linkedin.com" aria-label="LinkedIn">
                    <img src="/linkdin.svg" alt="LinkedIn" class="w-6 h-6">
                </a>
            </div>
            <img src="/brgs.svg" alt="BRGS Certified" class="w-24 mt-4"></div>


        </div>
    </div>

    
     <!-- Bottom Section -->
<div class="bg-[#003580] text-white text-center py-4 text-sm">
    <div class="max-w-6xl mx-auto flex flex-col md:flex-row items-center justify-between px-4 md:px-6 space-y-3 md:space-y-0">
        <!-- Links -->
        <div class="flex flex-wrap justify-center md:justify-start gap-4">
            <a href="#" class="hover:underline">Privacy Policy</a>
            <a href="#" class="hover:underline">Trading Terms</a>
            <a href="#" class="hover:underline">Terms of Use</a>
            <a href="#" class="hover:underline">GDPR</a>
        </div>

        <!-- Copyright Text -->
        <p class="text-xs md:text-sm text-gray-200">
            © 2025 New Forest Ice Cream Ltd. Registered in England & Wales. Company No: 2522236.
        </p>
    </div>
</div>

</footer>
