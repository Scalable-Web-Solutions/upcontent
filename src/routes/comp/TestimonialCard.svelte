<script lang="ts">
  export let name: string;
  export let role: string;
  export let avatar: string;
  export let text: string;
</script>

<div class="bg-gradient-to-br from-[#22262D] to-[#191C21] backdrop-blur-xl rounded-2xl shadow-2xl border border-white/10 p-10 flex flex-col justify-between min-h-[320px] md:min-h-[360px] w-full">
  <svg class="absolute -top-4 -left-4 w-16 h-16 text-white/10 pointer-events-none" fill="none" viewBox="0 0 48 48">
    <text x="0" y="38" font-size="64" font-family="serif" font-weight="bold">“</text>
  </svg>
  <p class="text-xl md:text-2xl text-gray-100 leading-relaxed z-10 relative mb-8 drop-shadow">{text}</p>
  <div class="flex items-center z-10 relative">
    <div class="w-12 h-12 rounded-full bg-gradient-to-br from-blue-500 to-purple-700 flex items-center justify-center text-white font-bold mr-4 shadow-lg text-2xl">{avatar}</div>
    <div>
      <div class="text-lg font-bold text-white">{name}</div>
      <div class="text-xs text-gray-400 font-medium">{role}</div>
    </div>
  </div>
</div>
