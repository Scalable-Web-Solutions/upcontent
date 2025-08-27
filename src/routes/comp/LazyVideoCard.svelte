<script lang="ts">
  import { onDestroy, onMount } from "svelte";
  let loaded = false;
  let root: HTMLElement;
  let observer: IntersectionObserver;
  let scrollContainer: any;

  import k from '$lib/assets/k.jpg'
  import ssone from '$lib/assets/Screenshot_21.png'
  import sstwo from '$lib/assets/Screenshot_22.png'

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
    const walk = (x - startX) * 1.3;
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

<div bind:this={root} class="bg-black min-h-screen w-full">
  {#if loaded}
    <section class="max-w-7xl mx-auto px-6 py-16">
      <!-- Heading -->
      <h1 class="text-white text-4xl font-bold mb-8">Behind the Scenes</h1>
      <!-- Scroller -->
      <!-- svelte-ignore a11y_no_static_element_interactions -->
      <div
        class="overflow-x-auto hide-sb cursor-grab"
        bind:this={scrollContainer}
        on:mousedown={handleMouseDown}
        on:mouseleave={handleMouseLeave}
        on:mouseup={handleMouseUp}
        on:mousemove={handleMouseMove}
      >
        <div class="flex flex-nowrap space-x-8 rounded-lg">
          <img class="rounded-lg size-160" src={k} alt="" />
          <img class="rounded-lg size-160" src={ssone} alt="" />
          <img class="rounded-lg size-160" src={sstwo} alt="" />
        </div>
      </div>
    </section>
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
