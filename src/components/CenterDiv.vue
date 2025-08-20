<template>
  <div class="w-full mx-auto">
    <p class="text-xs">Are you eligible to view my profile...?</p>
    <h2 class="text-lg font-bold text-[#ffe066] mb-2">
      Let's check your CSS... Center the Box
    </h2>
    <form @submit.prevent class="flex gap-2">
      <div class="mb-3">
        <label class="block text-gray-200 mb-1">display</label>
        <input
          v-model="display"
          class="w-full rounded px-2 outline-2 outline-white py-1 text-white"
          placeholder="Enter"
        />
      </div>
      <div class="mb-3">
        <label class="block text-gray-200 mb-1">justify-content</label>
        <input
          v-model="justifyContent"
          class="w-full rounded px-2 outline-2 outline-white py-1 text-white"
          placeholder="Enter"
        />
      </div>
      <div class="mb-3">
        <label class="block text-gray-200 mb-1">align-items</label>
        <input
          v-model="alignItems"
          class="w-full rounded px-2 outline-2 outline-white py-1 text-white"
          placeholder="Enter"
        />
      </div>
    </form>
    <div
      class="mt-2 h-36 w-full bg-[#181818] rounded relative"
      :style="parentStyle"
    >
      <div
        v-if="isCorrect"
        class="w-16 h-16 bg-[#ffe066] rounded flex items-center justify-center text-black font-bold text-lg shadow-lg transition-all duration-500"
      >
        🎉
      </div>
      <div
        v-else
        class="w-16 h-16 bg-[#ffe066] rounded flex items-center justify-center text-black font-bold text-lg shadow-lg opacity-50 transition-all duration-500"
      >
        Box
      </div>
    </div>
    <div v-if="isCorrect" class="text-green-400 text-center mt-1 font-semibold">
      Heyy ..! Are you wizard or what .. 🎯<button
        type="button"
        @click="emit('moveToNext')"
        class="text-3xl"
      >
        ⏩
      </button>
    </div>
    <div v-else class="text-red-500 text-center mt-1">
      Try the right flexbox values to center the box.
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from "vue";

const display = ref("");
const justifyContent = ref("");
const alignItems = ref("");
const emit = defineEmits(["moveToNext"]);
const isCorrect = computed(() => {
  const disp = display.value.trim().toLowerCase();
  return (
    (disp === "flex" || disp === "grid") &&
    justifyContent.value.trim().toLowerCase() === "center" &&
    alignItems.value.trim().toLowerCase() === "center"
  );
});

const parentStyle = computed(() => {
  return {
    display: display.value,
    justifyContent: justifyContent.value,
    alignItems: alignItems.value,
    transition: "all 0.5s",
  };
});
</script>
