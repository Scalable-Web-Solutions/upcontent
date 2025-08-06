<script lang="ts">
  import TestimonialCard from '../comp/TestimonialCard.svelte';

  const testimonials = [
    {
      name: "Balázs Kicks",
      role: "CEO, Sneakers Ltd",
      avatar: "B",
      text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolores molestias autem rerum, quas odio nemo animi officia eveniet minus assumenda praesentium earum ab. Ex quia sed, a voluptatem omnis corporis."
    },
    {
      name: "Starbucks Hungary",
      role: "Head of Content",
      avatar: "S",
      text: "Harum consequatur accusantium deserunt fuga modi exercitationem officiis laborum magnam impedit repellat laudantium, qui beatae in esse quia sed, accusamus ab tempora?"
    },
    {
      name: "OMI Asia Bistro",
      role: "Tuan, Owner",
      avatar: "O",
      text: "Consectetur tempora optio hic placeat numquam praesentium rerum et, dignissimos quod accusantium laborum labore iure ut aperiam. Ipsam officiis aliquid id aut."
    },
    {
      name: "Vivi Market",
      role: "CMO",
      avatar: "V",
      text: "Alias sequi modi earum, velit commodi ut dignissimos ipsum tenetur cumque, eligendi, obcaecati quaerat itaque animi. Inventore ea nesciunt placeat asperiores fugiat."
    },
    {
      name: "Domán Group",
      role: "Biz Dev",
      avatar: "D",
      text: "Iste, nemo ratione cum omnis sapiente suscipit nostrum inventore ad alias voluptate odio voluptas provident optio natus vitae exercitationem quasi architecto odit."
    },
  ];

  let current = 0;
  let startX: number | null = null;
  let dragging = false;
  let dx = 0;
  let cardEl: HTMLElement;

  function next() {
    current = (current + 1) % testimonials.length;
  }

  function prev() {
    current = (current - 1 + testimonials.length) % testimonials.length;
  }

  function onTouchStart(e: TouchEvent) {
    startX = e.touches[0].clientX;
    dragging = true;
    dx = 0;
  }

  function onTouchMove(e: TouchEvent) {
    if (!dragging || startX === null) return;
    dx = e.touches[0].clientX - startX;
  }

  function onTouchEnd() {
    if (!dragging) return;
    if (dx > 60) prev();
    else if (dx < -60) next();
    startX = null;
    dx = 0;
    dragging = false;
  }

  function onMouseDown(e: MouseEvent) {
    startX = e.clientX;
    dragging = true;
    dx = 0;
    window.addEventListener('mousemove', onMouseMove);
    window.addEventListener('mouseup', onMouseUp);
  }

  function onMouseMove(e: MouseEvent) {
    if (!dragging || startX === null) return;
    dx = e.clientX - startX;
  }

  function onMouseUp() {
    if (!dragging) return;
    if (dx > 60) prev();
    else if (dx < -60) next();
    startX = null;
    dx = 0;
    dragging = false;
    window.removeEventListener('mousemove', onMouseMove);
    window.removeEventListener('mouseup', onMouseUp);
  }
</script>

<section class="relative min-h-[70vh] flex flex-col items-center justify-center w-full bg-black py-20 overflow-hidden -mt-24">
  <div class="absolute inset-0 flex justify-center items-center pointer-events-none -z-10">
    <div class="w-[650px] h-[320px] rounded-full bg-gradient-to-tr from-blue-700/40 via-purple-600/20 to-blue-900/30 blur-3xl opacity-70"></div>
  </div>
  <p class="text-blue-500 font-semibold text-center text-lg mb-3 tracking-wide">Trusted by leading Hungarian brands</p>
  <h1 class="text-white text-4xl md:text-5xl font-bold mb-6 text-center drop-shadow-lg">
    What others have to say
  </h1>
  <div class="relative w-full flex justify-center items-center px-2 select-none">
    <!-- Left Arrow -->
    <button
      class="absolute -left-10 top-1/2 -translate-y-1/2 z-10 bg-[#181D28]/80 hover:bg-[#181D28] rounded-full p-2 shadow-lg transition border border-white/10"
      on:click={prev}
      aria-label="Previous"
    >
      <svg class="w-7 h-7" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M15 19l-7-7 7-7"/></svg>
    </button>
    <!-- Testimonial Card (with swipe/drag) -->
    <div
      class="mx-auto w-full max-w-2xl transition duration-500"
      bind:this={cardEl}
      on:touchstart={onTouchStart}
      on:touchmove={onTouchMove}
      on:touchend={onTouchEnd}
      on:mousedown={onMouseDown}
      style="transform: translateX({dx}px);"
    >
      <TestimonialCard
        name={testimonials[current].name}
        role={testimonials[current].role}
        avatar={testimonials[current].avatar}
        text={testimonials[current].text}
      />
    </div>
    <!-- Right Arrow -->
    <button
      class="absolute -right-10 top-1/2 -translate-y-1/2 z-10 bg-[#181D28]/80 hover:bg-[#181D28] rounded-full p-2 shadow-lg transition border border-white/10"
      on:click={next}
      aria-label="Next"
    >
      <svg class="w-7 h-7" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M9 5l7 7-7 7"/></svg>
    </button>
  </div>
  <!-- Dots / Indicators -->
  <div class="flex justify-center mt-8 gap-3">
    {#each testimonials as _, i}
      <button
        class="w-4 h-4 rounded-full border-2 {i === current ? 'bg-blue-600 border-blue-600 scale-110' : 'bg-gray-700 border-gray-400'} transition"
        on:click={() => (current = i)}
        aria-label={`Go to testimonial ${i + 1}`}
      />
    {/each}
  </div>
</section>
