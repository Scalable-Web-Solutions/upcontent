<script lang="ts">
  import { onDestroy, onMount } from "svelte";
  let loaded = false;
  let root: HTMLElement;
  let observer: IntersectionObserver;
  let scrollContainer: any;

  // Sample videos object for demonstration
  let videos = {
    afv: '7532162984584498445',
    e: '7532162984584498445',
    awdwad: '7532162984584498445',
    ererer: '7532162984584498445',
    rxgxgs: '7532162984584498445',
    cc: '7532162984584498445',
    reeexgxgs: '7532162984584498445',
  };

  let isDown = false;
  let startX = 0;
  let scrollLeft = 0;
  

  function handleMouseDown(e: MouseEvent) {
    isDown = true;
    scrollContainer.classList.add("cursor-grabbing");
    startX = e.pageX - scrollContainer.offsetLeft;
    scrollLeft = scrollContainer.scrollLeft;
  }
  function handleMouseLeave() {
    isDown = false;
    scrollContainer.classList.remove("cursor-grabbing");
  }
  function handleMouseUp() {
    isDown = false;
    scrollContainer.classList.remove("cursor-grabbing");
  }
  function handleMouseMove(e: MouseEvent) {
    if (!isDown) return;
    e.preventDefault();
    const x = e.pageX - scrollContainer.offsetLeft;
    const walk = (x - startX) * 1.3; // multiplier = drag speed
    scrollContainer.scrollLeft = scrollLeft - walk;
  }

  onMount(() => {
    if (typeof window !== "undefined" && root) {
      observer = new IntersectionObserver((entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            loaded = true;
            observer.disconnect();
          }
        });
      });
      observer.observe(root);
    }
  });

  onDestroy(() => {
    if (observer) observer.disconnect();
  });
</script>

<div bind:this={root} class="bg-black min-h-screen w-full overflow-y-hidden">
  {#if loaded}
    <!-- svelte-ignore a11y_no_static_element_interactions -->
    <div class="w-full overflow-x-auto overflow-y-hidden hide-sb cursor-grab" bind:this={scrollContainer} on:mousedown={handleMouseDown} on:mouseleave={handleMouseLeave} on:mouseup={handleMouseUp} on:mousemove={handleMouseMove}>
    <h1 class="text-white text-4xl font-bold ml-10 mt-10 absolute">What we offer</h1>
      <div class="flex flex-nowrap space-x-8 px-8 py-5 mt-20">
        {#each Object.entries(videos) as [key, value]}
          <div class="relative flex-shrink-0 rounded-[2.3rem] bg-black shadow-2xl overflow-hidden border border-gray-800"
            style="width: 300px; height: 600px;">
            <blockquote
              class="tiktok-embed w-full h-full"
              cite={`https://www.tiktok.com/@${key}/video/${value}`}
              data-video-id={value}
              style="width: 100%; height: 100%;"
            >
              <section class="flex flex-col justify-end h-full w-full">
                <!-- This section gets replaced by the TikTok embed -->
                <!-- svelte-ignore a11y_consider_explicit_label -->
                <a target="_blank" title={`@${key}`} href={`https://www.tiktok.com/@${key}?refer=embed`} class="text-white"></a>
                <span class="p-4 text-white text-2xl font-bold bg-gradient-to-t from-black/70 to-transparent rounded-b-[2.3rem]">
                  TikTok Placeholder<br />{key}
                </span>
              </section>
            </blockquote>
            <script async src="https://www.tiktok.com/embed.js"></script>
          </div>
        {/each}
      </div>
    </div>
  {/if}
</div>

<style>
  .hide-sb{
    &::-webkit-scrollbar {
      display: none;
    }
    -ms-overflow-style: none;
    scrollbar-width: none;
  }
  .cursor-grabbing {
    cursor: grabbing !important;
    user-select: none;
  }
</style>

