<script lang='ts'>
  import bg from '../../assets/bg.png';
  import TestimonialCard from '../comp/TestimonialCard.svelte';
</script>

<div class="relative bg-black min-h-screen pt-20">

  <div class="max-w-7xl mx-auto px-4 sm:px-6 relative z-10">
    <div class="flex flex-col md:flex-row items-center justify-between mb-10 md:mb-16">
      <h1 class="text-white text-4xl md:text-5xl font-bold tracking-tight mt-6 md:mt-10">
        What others have to say
      </h1>
    </div>

    <div class="w-full">
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6 md:gap-8">
        <!-- First card: big on desktop, regular on mobile -->
        <TestimonialCard grid="lg:col-span-2 lg:row-span-2" />
        <TestimonialCard grid="" />
        <TestimonialCard grid="lg:col-span-2" />
        <TestimonialCard grid="" />
        <!-- Add more as needed -->
      </div>
    </div>
  </div>
</div>
