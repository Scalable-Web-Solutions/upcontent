<script lang="ts">
    import cc from '../../assets/cc.mp4'
    import { name } from '$lib/util';
    
    const scrollToContact = () => {
    const contactSection = document.getElementById('contact');
    if (contactSection) {
      contactSection.scrollIntoView({ behavior: 'smooth' });
    }
  }
</script>

<div class="main h-screen w-screen overflow-hidden">
  <div class="main relative h-full w-full">
        <video
          class="absolute inset-0 object-cover -z-10 blur-xs scale-105 h-full w-full"
          src={cc}
          autoPlay
          loop
          controls={false}
          muted
        ></video>
        <div class="absolute inset-0 z-10 bg-gradient-to-t from-black/100 to-transparent"></div>
        <div class="absolute inset-0 z-10 flex flex-col items-center justify-center gap-5 px-4 md:px-0">
          <h1
            class="text-white font-semibold leading-[1.1] text-center text-4xl sm:text-5xl md:text-[75px]"
          >
            Redesign your <br /> content with {name}
          </h1>
          <p
            class="text-white text-base sm:text-lg text-center max-w-full md:max-w-[35%]"
          >
            {name} is Hungary’s leading content agency, trusted by top brands for our hands-on, done-for-you approach. No extra steps, no hidden costs, 222222222222222222222222222222222222222just proven, high-performing content delivered exactly when you need it.
          </p>
          <button
            data-cta="hero-free-preview"
            class="bg-white text-black px-8 py-3 rounded-full font-semibold text-base sm:text-lg"
            on:click={() => scrollToContact()}

          >
            Get My Free Preview
          </button>
        </div>
        <div class="absolute bottom-8 left-1/2 transform -translate-x-1/2 text-white text-sm font-semibold animate-pulse select-none cursor-default z-20">
            scroll
        </div>

    </div>
</div>
