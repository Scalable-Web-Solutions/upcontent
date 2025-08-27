<script>
  import { name } from "$lib/util";
</script>

<footer class="bg-black">
  <div class="max-w-7xl mx-auto px-6 py-12">
    <div class="flex flex-col md:flex-row md:justify-between md:items-center gap-10">

      <!-- Logo + Tagline -->
      <div class="flex flex-col gap-2">
        <a href="/" class="flex items-center gap-2">
          <span class="text-2xl font-bold text-white tracking-tight">{name}</span>
        </a>
        <p class="text-gray-400 text-sm max-w-xs">
          Creating quality media that people love.
        </p>
      </div>

      <!-- Footer Links -->
      <div class="grid grid-cols-2 sm:grid-cols-3 gap-8">
        <div>
          <h4 class="text-white text-sm font-semibold mb-3">Company</h4>
          <ul class="space-y-2">
            <li><a href="#about" class="text-gray-400 hover:text-white transition">About Us</a></li>
            <li><a href="#contact" class="text-gray-400 hover:text-white transition">Contact</a></li>
          </ul>
        </div>
        <div>
          <h4 class="text-white text-sm font-semibold mb-3">Services</h4>
          <ul class="space-y-2">
            <li><a href="/websites" class="text-gray-400 hover:text-white transition">Content</a></li>
          </ul>
        </div>
        <div>
          <h4 class="text-white text-sm font-semibold mb-3">Social</h4>
          <ul class="space-y-2">
            <li>
              <a href="https://instagram.com/kaytee.media" target="_blank" class="text-gray-400 hover:text-white transition">
                Instagram
              </a>
            </li>
            <li>
              <a href="https://tiktok.com/@kaytee.media" target="_blank" class="text-gray-400 hover:text-white transition">
                TikTok
              </a>
            </li>
          </ul>
        </div>
      </div>
    </div>

    <!-- Divider -->
    <div class="border-t border-white/10 my-8"></div>

    <!-- Bottom Bar -->
    <div class="flex flex-col md:flex-row justify-between items-center gap-4">
      <span class="text-xs text-gray-500">
        &copy; {new Date().getFullYear()} {name}.
      </span>
      <div class="flex gap-3">
        <a href="/privacy" class="text-xs text-gray-400 hover:text-white">Privacy Policy</a>
        <a href="/terms" class="text-xs text-gray-400 hover:text-white">Terms of Service</a>
      </div>
    </div>
  </div>
</footer>
