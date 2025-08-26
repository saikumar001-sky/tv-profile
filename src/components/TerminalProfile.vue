<template>
  <section class="text-left">
    <div class="flex items-center gap-1 mb-2 bg-gray-600 p-2 rounded-lg">
      <div class="w-3 h-3 rounded-full bg-red-500"></div>

      <div class="w-3 h-3 rounded-full bg-yellow-500"></div>
      <div class="w-3 h-3 rounded-full bg-green-500"></div>
      <p class="text-[9px] md:text-xs mb-0">
        Note: Type <span class="font-semibold text-yellow-500">help</span> to
        get all commands
      </p>
    </div>

    <div
      id="terminalContainer"
      class="overflow-y-auto h-[200px] md:h-[250px] mb-4 scroll-mb-1.5"
    >
      <div v-for="(entry, idx) in history" :key="idx" class="mb-1">
        <div class="flex items-baseline">
          <span class="text-[10px] md:text-sm text-left">PS C: \profile\sai&gt;&nbsp;</span>
          <span class="text-xs font-mono text-green-300">{{
            entry.input
          }}</span>
        </div>
        <div v-if="entry.type === 'help'">
          <div class="my-1 text-xs">Available commands:</div>
          <table class="text-xs ms-5 w-auto border-collapse">
            <tbody>
              <tr v-for="cmd in commands" :key="cmd.name">
                <td class="pr-2 align-top font-semibold text-yellow-400">
                  {{ cmd.name }}
                </td>
                <td class="pl-2 text-gray-200">: {{ cmd.desc }}</td>
              </tr>
            </tbody>
          </table>
        </div>
        <div v-else-if="entry.type === 'command'">
          <div class="mt-1 text-xs text-gray-100 rounded p-2 w-fit">
            <div v-if="entry.input === 'about'">
              <span class="font-bold text-yellow-300">About:</span>
              <ul class="list-disc pl-5 mt-1 space-y-1">
                <li>
                  3 years of experience as a Frontend Developer (HTML, CSS,
                  JavaScript, Vue.js)
                </li>
                <li>Flexible and adaptable with any frontend framework</li>
                <li>
                  Skilled in integrating with RESTful APIs and real-time data
                  (WebSockets)
                </li>
                <li>Familiar with modern tools: Vite, Vuetify, PrimeVue</li>
                <li>
                  Proficient in reusable Vue 3 components, state management, and
                  NPM packages
                </li>
              </ul>
            </div>
            <div v-else-if="entry.input === 'experience'">
              <span class="font-bold text-yellow-300">Experience:</span>
              <ul class="list-disc pl-5 mt-1 space-y-1">
                <li>
                  <span class="font-semibold">Frontend Devloper</span><br />
                  HCA Helathcare | Hyderabad, India<br />
                  <span class="text-xs text-gray-400">July 2025 – Present</span>
                </li>
                <li>
                  <span class="font-semibold"
                    >Senior Web Application Developer</span
                  ><br />
                  SoftDevels Private Limited | Pune, India<br />
                  <span class="text-xs text-gray-400"
                    >Jul 2024 – June 2025</span
                  >
                </li>
                <li>
                  <span class="font-semibold">Senior Application Developer</span
                  ><br />
                  Bestinet Sdn Bhd (Malaysia) | Kuala Lumpur, Malaysia<br />
                  <span class="text-xs text-gray-400"
                    >Sep 2023 – June 2024</span
                  >
                </li>
                <li>
                  <span class="font-semibold">Web Application Developer</span
                  ><br />
                  SoftDevels Private Limited | Pune, India
                </li>
              </ul>
            </div>
            <div v-else-if="entry.input === 'education'">
              <span class="font-bold text-yellow-300">Education:</span>
              <ul class="list-disc pl-5 mt-1 space-y-1">
                <li>
                  <span class="font-semibold"
                    >Bachelor of Technology (BTech)</span
                  ><br />
                  Jawaharlal Nehru Technological University, Ananthapur (JNTUA
                  CEA)<br />
                  <span class="text-xs text-gray-400">Jul 2019 – Jun 2022</span>
                </li>
              </ul>
            </div>
            <div v-else-if="entry.input === 'projects'">
              <span class="font-bold text-yellow-300">Projects:</span>
              <ul class="list-disc pl-5 mt-1 space-y-2">
                <li>
                  <span class="font-semibold"
                    >QQPAY (Remittance Application)</span
                  ><br />
                  Multi-portal app for cross-border payments, live exchange
                  rates, and secure, compliant transactions.
                </li>
                <li>
                  <span class="font-semibold">SP Commission Portal</span><br />
                  Commission management system for onboarding, tracking, and
                  referral payouts with user role verification and wallet
                  integration.
                </li>
                <li>
                  <span class="font-semibold"
                    >Electronic Health Records (EHR)</span
                  ><br />
                  Healthcare platform with Aadhaar/ABHA integration, push
                  notifications, and multi-role activity mapping.
                </li>
                <li>
                  <span class="font-semibold">DevEase Developer Toolkit</span
                  ><br />
                  Toolkit with HTML/JS compilers, JWT decoders, image
                  compressors, Base64 & UUID generators.<br />
                  <a href="https://github.com/saikumar001-sky/Devguru" class="text-blue-400 underline" target="_blank"
                    >View In GitHub</a
                  >
                  |
                  <a href="https://main--dev-ease-05a89e.netlify.app/" class="text-blue-400 underline" target="_blank"
                    >App Link</a
                  >
                </li>
                <li>
                  <span class="font-semibold">Gold Scheme</span><br />
                  Customer management system for gold shop owners.<br />
                  <a href="https://github.com/saikumar001-sky/Gold-Scheme" class="text-blue-400 underline" target="_blank"
                    >View in GitHub</a
                  >
                </li>
              </ul>
            </div>
            <div v-else-if="entry.input === 'npm packages'">
              <span class="font-bold text-yellow-300">NPM Packages:</span>
              <ul class="list-disc pl-5 mt-1 space-y-2">
                <li>
                  <span class="font-semibold">countryFlags-vue</span><br />
                  Vue 3 component package to display country flags by ISO 2 or
                  ISO 3 codes.<br />
                  <a href="https://github.com/saikumar001-sky/countryflags-vue" class="text-blue-400 underline" target="_blank"
                    >View in GitHub</a
                  >
                  |
                  <a href="https://www.npmjs.com/package/countryflags-vue" class="text-blue-400 underline" target="_blank"
                    >View in NPM</a
                  >
                </li>
                <li>
                  <span class="font-semibold">UUID Generator</span><br />
                  JavaScript npm package to generate UUID v4.<br />
                  <a href="https://github.com/saikumar001-sky/uuid-generator" class="text-blue-400 underline" target="_blank"
                    >View in GitHub</a
                  >
                  |
                  <a href="https://www.npmjs.com/package/uuidx4-generator" class="text-blue-400 underline" target="_blank"
                    >View in NPM</a
                  >
                </li>
                <li>
                  <span class="font-semibold">jwt-decoder-lib</span><br />
                  JavaScript npm package to decode JSON Web Tokens (JWT).<br />
                  <a href="https://github.com/saikumar001-sky/token-decoder" class="text-blue-400 underline" target="_blank"
                    >View in GitHub</a
                  >
                  |
                  <a href="https://www.npmjs.com/package/jwt-decoder-lib" class="text-blue-400 underline" target="_blank"
                    >View in NPM</a
                  >
                </li>
              </ul>
            </div>
            <div v-else-if="entry.input === 'skills'">
              <span class="font-bold text-yellow-300">Tech Skills:</span>
              <ul class="list-disc pl-5 mt-1 space-y-1">
                <li>
                  <span class="font-semibold">Languages:</span> JavaScript,
                  HTML, CSS, Python
                </li>
                <li>
                  <span class="font-semibold">Frontend Frameworks:</span> Vue.js
                  (Vue 2 & Vue 3), React
                </li>
                <li>
                  <span class="font-semibold">Component Frameworks:</span>
                  Vuetify, PrimeVue, Quasar, Material UI
                </li>
                <li>
                  <span class="font-semibold">Build Tools:</span> Vite, Vue CLI,
                  Webpack, NPM
                </li>
                <li>
                  <span class="font-semibold">CSS Frameworks:</span> Tailwind
                  CSS, Bootstrap, SCSS
                </li>
                <li>
                  <span class="font-semibold">Version Control:</span> Git,
                  GitLab, GitHub, Bitbucket
                </li>
                <li><span class="font-semibold">Editors/IDEs:</span> VSCode</li>
                <li>
                  <span class="font-semibold">Operating Systems:</span> Ubuntu,
                  Linux, Windows
                </li>
                <li>
                  <span class="font-semibold">Backend/DevOps:</span> FastAPI,
                  Docker, NGINX, SSL, AWS EC2
                </li>
              </ul>
            </div>
          </div>
        </div>
        <div v-else-if="entry.type === 'error'">
          <div class="mt-1 bg-red-900 text-xs text-red-200 rounded p-2 w-fit">
            {{ entry.output }}
          </div>
        </div>
      </div>
      <div class="flex items-baseline">
        <span class="text-[10px] md:text-xs text-left">PS C: \profile\sai&gt;&nbsp;</span>
        <input
          name="userInput"
          :autofocus="true"
          class="user-input !text-xs"
          v-model="userInput"
          @keydown.enter="handleEnter"
          @blur="onBlur"
          ref="inputRef"
        />
      </div>
    </div>
  </section>
</template>
<script setup>
import { ref, nextTick } from "vue";

const userInput = ref("");
const inputRef = ref(null);
const history = ref([]);

const commands = [
  { name: "about", desc: "know more about me" },
  { name: "experience", desc: "yup ...! i got few years of exp" },
  { name: "education", desc: "offcourse i'm educated :)" },
  { name: "projects", desc: "did some want to see" },
  { name: "npm packages", desc: "NPM : No Problem Man ..." },
  { name: "skills", desc: "skills skills skills skills ...etc" },
];

function handleEnter() {
  const input = userInput.value.trim().toLowerCase();
  if (!input) {
    userInput.value = "";
    nextTick(() => {
      if (inputRef.value) inputRef.value.focus();
    });
    return;
  }
  if (input === "help") {
    history.value.push({ input: userInput.value.trim(), type: "help" });
  } else if (input === "cls" || input === "clear") {
    history.value.length = 0;
  } else if (commands.some((cmd) => cmd.name === input)) {
    history.value.push({ input, type: "command" });
  } else {
    history.value.push({
      input: userInput.value.trim(),
      type: "error",
      output: `Command not found: '${userInput.value.trim()}'. Please type help to get commands.`,
    });
  }
  userInput.value = "";
  const terminalContainer = document.getElementById("terminalContainer");
  // allow 1px inaccuracy by adding 1
  const isScrolledToBottom =
    terminalContainer.scrollHeight - terminalContainer.clientHeight <=
    terminalContainer.scrollTop + 1;

  nextTick(() => {
    if (inputRef.value) inputRef.value.focus();
    if (isScrolledToBottom) {
      terminalContainer.scrollTop = terminalContainer.scrollHeight;
    }
  });
}

function onBlur() {
  // Always keep focus for terminal-like experience
  nextTick(() => {
    if (inputRef.value) inputRef.value.focus();
  });
}
</script>

<style>
.user-input {
  all: unset;
}
</style>
