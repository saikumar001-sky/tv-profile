<template>
  <div
    class="flex flex-col items-center justify-start rounded-xl md:p-8 pt-8 relative"
  >
    <!-- Mac Terminal style  -->
    <div class="flex">
      <div class="text-blue-200 mt-1">console.</div>
      <div class="text-yellow-300 mt-1">log</div>
      <span class="mt-1"> ("</span>
      <div class="w-full max-w-[430px] h-12 overflow-hidden relative">
        <div class="flex flex-col animate-scroll-vertical">
          <div
            class="text-[#ffe066] font-mono text-xs md:text-lg text-center tracking-wide py-2 pb-3"
          >
            Hello i'm sAi..👦🏻 !
          </div>
          <div
            class="text-red-500 font-mono text-xs md:text-lg text-center tracking-wide py-2"
          >
            i'm a FrOnTeND dEV👨🏻‍💻
          </div>
          <div
            class="text-[#6966ff] font-mono text-xs md:text-lg text-center tracking-wide py-2"
          >
            Here my SToRy..📜
          </div>
          <div
            class="text-[#82ff66] font-mono text-xs md:text-lg text-center tracking-wide py-2 ]"
          >
            click on PoWeR BtN ⏻
          </div>
        </div>
      </div>
      <span class="mt-1"> ")</span>
    </div>
    <div class="md:mt-12">
      <span class="text-3xl md:text-7xl">🧐</span>
      <p class="text-sm">
        Have you found the
        <span class="text-red-500">misalignment in above text</span>...<span
          class="md:text-3xl text-amber-500"
          >?</span
        >
      </p>
      <p class="text-yellow-400 font-semibold text-sm font-serif">
        " This div isn’t centered… neither is my life. "
      </p>
      <div class="mt-2">
        <button
          type="button"
          @click="emit('moveToNext')"
          class="cursor-pointer text-3xl text-amber-500"
        >
          ⏩
        </button>
      </div>
    </div>
  </div>
</template>
<script setup>
const emit = defineEmits(['moveToNext']);
</script>
<style scoped>
@keyframes scroll-vertical {
  0% {
    transform: translateY(0);
  }
  20% {
    transform: translateY(0);
  }
  25% {
    transform: translateY(-48px);
  }
  45% {
    transform: translateY(-48px);
  }
  50% {
    transform: translateY(-96px);
  }
  70% {
    transform: translateY(-96px);
  }
  75% {
    transform: translateY(-144px);
  }
  95% {
    transform: translateY(-144px);
  }
  100% {
    transform: translateY(0);
  }
}
.animate-scroll-vertical {
  animation: scroll-vertical 6s cubic-bezier(0.77, 0, 0.18, 1) infinite;
}
</style>
