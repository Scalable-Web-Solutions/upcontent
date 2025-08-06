<script>
  let isOpen = false;

  function toggleMenu() {
    isOpen = !isOpen;
  }

  const scrollToContact = () => {
    const contactSection = document.getElementById('contact');
    if (contactSection) {
      contactSection.scrollIntoView({ behavior: 'smooth' });
    }
  }
</script>

<nav class="w-full h-[120px] fixed top-0 left-0 right-0 text-white z-50">
  <div class="max-w-7xl mx-auto h-16 flex items-center justify-between px-6 md:px-10">
    <!-- Logo -->
    <div class="flex items-center gap-5">
      <h1 class="text-2xl font-bold cursor-pointer">UpContent</h1>
    </div>

    <!-- Desktop Links -->
    <div class="hidden md:flex gap-8 font-semibold">
      <a href="#" class="hover:text-purple-400 transition">Home</a>
      <a href="#" class="hover:text-purple-400 transition">About</a>
      <a href="#" class="hover:text-purple-400 transition">What we offer</a>
      <a href="#" class="hover:text-purple-400 transition">Testimonials</a>
      <a href="#" class="hover:text-purple-400 transition">Contact</a>
    </div>

    <!-- CTA Button -->
    <div class="hidden md:block">
      <button on:click={() => scrollToContact()} data-cta="nav-free-preview" class="bg-white text-black px-8 py-2 rounded-full font-semibold hover:bg-gray-200 transition">

        Get A Free Preview
      </button>
    </div>

    <!-- Mobile Hamburger -->
    <button
      class="md:hidden flex items-center justify-center w-10 h-10 focus:outline-none"
      on:click={toggleMenu}
      aria-label="Toggle menu"
    >
      <svg
        class="w-6 h-6 text-white"
        fill="none"
        stroke="currentColor"
        viewBox="0 0 24 24"
        xmlns="http://www.w3.org/2000/svg"
      >
        {#if !isOpen}
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 8h16M4 16h16"></path>
        {:else}
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
        {/if}
      </svg>
    </button>
  </div>

  <!-- Mobile Menu -->
  {#if isOpen}
    <div class="md:hidden bg-black/90 backdrop-blur-sm px-6 py-4 space-y-4 font-semibold">
      <a href="#" class="block hover:text-purple-400 transition">Home</a>
      <a href="#" class="block hover:text-purple-400 transition">About</a>
      <a href="#" class="block hover:text-purple-400 transition">What we offer</a>
      <a href="#" class="block hover:text-purple-400 transition">Testimonials</a>
      <a href="#" class="block hover:text-purple-400 transition">Contact</a>
      <button on:click={() => scrollToContact()} class="w-full bg-white text-black py-2 rounded-full font-semibold hover:bg-gray-200 transition">
        Get A Free Preview
      </button>
    </div>
  {/if}
</nav>
