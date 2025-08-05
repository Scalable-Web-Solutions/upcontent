<script lang='ts'>
  import bg from '../../assets/bg.png'
    import TestimonialCard from '../comp/TestimonialCard.svelte';
</script>

<div class="bg-black min-h-screen">
  <img src={bg} alt="" class="w-full h-full object-cover absolute -z10">

  <div class="max-w-7xl mx-auto px-6 relative z-10">
    <div class="flex flex-col md:flex-row items-center justify-between mb-16">
      <h1 class="text-white text-4xl md:text-5xl font-bold tracking-tight">
        What others have to say
      </h1>
      <button class="mt-4 md:mt-0 px-6 py-2 rounded-full bg-white text-black font-semibold shadow hover:bg-gray-100 transition">
        Contact
      </button>
    </div>

    <div class="columns-1 sm:columns-2 lg:columns-3 gap-6 space-y-6"> 
      <div class="break-inside-avoid">
        <TestimonialCard/>
        <TestimonialCard/>
        <TestimonialCard/>
        <TestimonialCard/>
        <TestimonialCard/>
        <TestimonialCard/>
        <TestimonialCard/>
        <TestimonialCard/>
      </div>
    </div>
  </div>
</div>
