<script lang="ts">
  import kane from '../../assets/kane.png'
</script>

<section class="py-20 bg-black">
  <div class="max-w-7xl mx-auto px-6">
    <div class="grid lg:grid-cols-2 gap-16 items-center">
      <!-- Left Column - Text -->
      <div>
        <div class="inline-block bg-blue-900/30 text-blue-400 px-4 py-2 rounded-full text-sm font-medium mb-6">
          About UpContent
        </div>
        <h2 class="text-4xl md:text-5xl font-bold text-white mb-6 leading-tight">
          Crafting content with
          <span class="text-blue-400"> Quality</span>
        </h2>
        <p class="text-lg text-gray-300 mb-8 leading-relaxed">
          We believe that exceptional content drives exceptional results. Our team of strategists,
          designers, and content creators work together to reimagine how brands communicate with
          their audiences in the digital age.
        </p>

        <div class="space-y-6 mb-8">
          <div class="flex items-start">
            <div>
              <h3 class="font-semibold text-white mb-2">Strategic Approach</h3>
              <p class="text-gray-300">
                Every piece of content is crafted with purpose,
                targeting specific goals and audience needs.
              </p>
            </div>
          </div>

          <div class="flex items-start">
            <div>
              <h3 class="font-semibold text-white mb-2">Collaborative Process</h3>
              <p class="text-gray-300">
                We work closely with your team to ensure every
                solution aligns with your brand vision and objectives.
              </p>
            </div>
          </div>

          <div class="flex items-start">
            <div>
              <h3 class="font-semibold text-white mb-2">Proven Results</h3>
              <p class="text-gray-300">
                Our data-driven methodology has helped hundreds
                of brands achieve measurable content success.
              </p>
            </div>
          </div>
        </div>

        <button class="group inline-flex items-center bg-white text-black px-6 py-3 rounded-full font-medium hover:bg-gray-200 transition-all duration-300">
          Get A Free Preview
        </button>
      </div>

      <!-- Right Column - Image -->
      <div class="relative">
        <div class="relative rounded-2xl overflow-hidden shadow-2xl">
          <img
            src={kane}
            alt="Team working on content strategy"
            class="w-full h-[600px] object-cover shadow-2xl shadow-white"
          />
          <div class="absolute inset-0 bg-gradient-to-t from-black/60 to-transparent"></div>
        </div>

        <!-- Floating Stats Cards (Dark) -->
        <div class="absolute -left-6 top-20 bg-gray-900/90 p-6 rounded-xl shadow-lg border border-gray-800">
          <div class="text-3xl font-bold text-white mb-1">25+</div>
          <div class="text-sm text-gray-400">Projects Completed</div>
        </div>

        <div class="absolute -right-6 bottom-20 bg-gray-900/90 p-6 rounded-xl shadow-lg border border-gray-800">
          <div class="text-3xl font-bold text-blue-400 mb-1">98%</div>
          <div class="text-sm text-gray-400">Client Satisfaction</div>
        </div>
      </div>
    </div>
  </div>
</section>
