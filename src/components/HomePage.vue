<template>
  <div class="flex justify-center items-center h-[100vh] main-bg w-full">
    <div class="relative h-[70vh] w-full md:w-3/5">
      <div
        class="absolute w-full z-40 h-full bg-gray-500 tv-frame flex tv-shadow gap-2 p-12 rounded-4xl"
      >
        <!-- TV screen Area  -->
        <div
          class="bg-gray-700 z-40 tv-shadow h-full outline-[12px] outline-gray-900 w-full p-6 m-2 border-[20px] border-gray-800 rounded-4xl"
        >
          <div
            v-if="stage === 1"
            class="flex flex-col items-center justify-center h-full"
          >
            <p class="text-center text-7xl">📺</p>
            <div class="text-center text-yellow-500 font-bold text-2xl mb-4">
              Welcome to my TV Profile
            </div>
            <p>click on the power button to start</p>
          </div>
          <div>
            <TerminalScreen @moveToNext="moveToNext" v-if="stage === 2" />
          </div>
          <div>
            <CenterDiv @moveToNext="() => (stage = 4)" v-if="stage === 3" />
          </div>
          <div>
            <TerminalProfile v-if="stage === 4" />
          </div>
        </div>
        <!-- TV control Buttons  -->
        <div class="h-full w-[100px]">
          <!-- TV speaker -->
          <div
            class="bg-gray-400 h-[200px] p-6 tv-shadow speaker-mesh border-2 border-gray-500 rounded-4xl mx-auto mb-4"
          ></div>
          <!-- TV Volume Control -->
          <div>
            <div
              class="tv-accessories border-[6px] border-gray-600 h-[30px] w-[30px] rounded-full mb-2 mx-auto tv-shadow"
            ></div>
            <div
              class="tv-accessories border-[6px] border-gray-600 h-[30px] w-[30px] rounded-full mb-2 mx-auto tv-shadow"
            ></div>
            <div
              class="tv-accessories border-[6px] border-gray-600 h-[30px] w-[30px] rounded-full mb-2 mx-auto tv-shadow"
            ></div>
          </div>
          <!-- TV power button -->
          <div>
            <button
              title="Power Button"
              @click="switchon"
              class="border-[6px] animate-bounce cursor-pointer border-gray-600 h-[40px] w-[40px] rounded-full mt-8 mx-auto tv-shadow"
            >
              <div
                :class="startTv ? 'bg-green-500' : 'bg-red-500'"
                class="w-full h-full flex justify-center rounded-full border-4 border-white tv-shadow"
              >
                <div class="w-[4px] h-[10px] bg-white"></div>
              </div>
            </button>
          </div>
        </div>
      </div>
      <div
        class="tv-shadow tv-accessories absolute z-0 top-[-30px] left-[50%] right-[-50%] w-[100px] h-[100px] rounded-full bg-gray-500"
      >
        <div
          class="bg-gray-500 absolute tv-accessories tv-frame rounded-full z-0 -top-[70px] left-[100px] h-[100px] rotate-45 w-[5px]"
        ></div>
        <div
          class="bg-gray-500 absolute z-0 tv-accessories tv-frame rounded-full -top-[70px] right-[100px] h-[100px] -rotate-[45deg] w-[5px]"
        ></div>
      </div>
      <div>
        <div
          class="bg-gray-500 tv-shadow tv-accessories absolute z-0 -bottom-[50px] left-[100px] h-[90px] rotate-[45deg] w-[30px] rounded-4xl"
        ></div>
        <div
          class="bg-gray-500 tv-shadow tv-accessories absolute z-0 -bottom-[50px] right-[100px] h-[90px] -rotate-[45deg] w-[30px] rounded-4xl"
        ></div>
      </div>
    </div>
  </div>
</template>
<script setup>
import { ref } from "vue";
import TerminalScreen from "./TerminalScreen.vue";
import CenterDiv from "./CenterDiv.vue";
import TerminalProfile from "./TerminalProfile.vue";
const startTv = ref(false);
const stage = ref(1);
const moveToNext = () => {
  stage.value = 3;
};
const switchon = () => {
  startTv.value = !startTv.value;
  stage.value = startTv.value ? 2 : 1;
};
console.log("TerminalScreen component loaded");
</script>
<style scoped>
.main-bg {
  background-image: url("../assets/bg2.png");
  background-size: contain;
  background-position:top;
  background-color: #181818;
}
.tv-shadow {
  box-shadow: rgba(0, 0, 0, 0.17) 0px -23px 25px 0px inset,
    rgba(0, 0, 0, 0.15) 0px -36px 30px 0px inset,
    rgba(0, 0, 0, 0.1) 0px -79px 40px 0px inset, rgba(0, 0, 0, 0.06) 0px 2px 1px,
    rgba(0, 0, 0, 0.09) 0px 4px 2px, rgba(0, 0, 0, 0.09) 0px 8px 4px,
    rgba(0, 0, 0, 0.09) 0px 16px 8px, rgba(0, 0, 0, 0.09) 0px 32px 16px;
}
.tv-screen-shadow {
  box-shadow: rgba(50, 50, 93, 0.25) 0px 30px 60px -12px inset,
    rgba(0, 0, 0, 0.3) 0px 18px 36px -18px inset;
  /* box-shadow: rgba(0, 0, 0, 0.17) 0px -23px 25px 0px inset,
    rgba(0, 0, 0, 0.15) 0px -36px 30px 0px inset,
    rgba(0, 0, 0, 0.1) 0px -79px 40px 0px inset, rgba(0, 0, 0, 0.06) 0px 2px 1px,
    rgba(0, 0, 0, 0.09) 0px 4px 2px, rgba(0, 0, 0, 0.09) 0px 8px 4px,
    rgba(0, 0, 0, 0.09) 0px 16px 8px, rgba(0, 0, 0, 0.09) 0px 32px 16px; */
}
.speaker-mesh {
  background-image: url("../assets/mesh.jpg");
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  box-shadow: rgba(0, 0, 0, 0.1) 0px 2px 1px, rgba(0, 0, 0, 0.09) 0px 4px 2px,
    rgba(0, 0, 0, 0.09) 0px 8px 4px, rgba(0, 0, 0, 0.09) 0px 16px 8px,
    rgba(0, 0, 0, 0.09) 0px 32px 16px;
}
.tv-frame {
  background-image: url("../assets/tv.jpeg");
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}
.tv-accessories {
  background-image: url("../assets/tv2.jpg");
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}
</style>
