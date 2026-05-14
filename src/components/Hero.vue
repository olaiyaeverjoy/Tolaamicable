<script setup>
import logo from "../assets/logo/logo.png";
import { ref, shallowRef, onMounted, nextTick} from "vue";
import video1 from '../assets/videos/construct.mp4'
import video2 from '../assets/videos/construction2.bg.mp4'


// const videos = [
//   "../assets/videos/construction2.bg.mp4",
//   "../assets/videos/construction.bg.mp4",
// ];

// const currentIndex = ref(0);

// const nextVideo = () => {
//   currentIndex.value = (currentIndex.value + 1) % videos.length;
// };

const isOpen = ref(false);

const toggleMenu = () => {
  isOpen.value = !isOpen.value;
};


const videos = [video1, video2]

const activeVideo = ref(0)

// 
const firstVideoRef = shallowRef(null)
const secondVideoRef = shallowRef(null)

const playNext = () => {
  activeVideo.value = activeVideo.value === 0 ? 1 : 0

  const activeEl =
    activeVideo.value === 0 ? firstVideoRef.value : secondVideoRef.value

  activeEl.play()
}

onMounted(() => {
  firstVideoRef.value.play()
})
// const videoRef = ref(null)
// const currentIndex = ref(0)

// const nextVideo = (e) => {
//   currentIndex.value = (currentIndex.value + 1) % videos.length

//   // nextTick(() => {
//   //   videoRef.value?.load()   // reloads the new <source>
//   //   videoRef.value?.play()   // then plays it
//   // })
//   e.target.src = videos[currentIndex.value]
//   e.target.play()
// }

//correct this scrolling block to an array and imbed every section into it 
const scrollToServices = () => {
  document.getElementById('services').scrollIntoView({
    behavior: 'smooth'
  })
}
const scrollToProjects = () => {
  document.getElementById('projects').scrollIntoView({
    behavior: 'smooth'
  })
}
</script>

<template>
  <section class="relative h-[78vh] w-full overflow-hidden">
    <!-- <video
      ref="videoRef"
      
      autoplay
      muted
      playsinline
      class="absolute inset-0 w-full h-full object-cover"
      @ended="nextVideo"
    >
      <source :src="videos[currentIndex]" type="video/mp4" />
    </video> -->
    <div class="absolute inset-0 w-full h-full overflow-hidden">
    <!-- Video 1 -->
    <video
      ref="firstVideoRef"
      :src="videos[0]"
      muted
      playsinline
      preload="auto"
      class="absolute inset-0 w-full h-full object-cover transition-opacity duration-700"
      :class="activeVideo === 0 ? 'opacity-100 z-10' : 'opacity-0 z-0'"
      @ended="playNext"
    />

    <!-- Video 2 -->
    <video
      ref="secondVideoRef"
      :src="videos[1]"
      muted
      playsinline
      preload="auto"
      class="absolute inset-0 w-full h-full object-cover transition-opacity duration-700"
      :class="activeVideo === 1 ? 'opacity-100 z-10' : 'opacity-0 z-0'"
      @ended="playNext"
    />
  </div>


    <nav class="relative z-20 w-full border-t py-6">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div
          class="flex justify-between items-center gap-8"
          data-aos="fade-down"
        >
          <img class="w-[99px] h-[35px] object-contain" :src="logo" alt="" />

          <ul class="hidden sm:flex gap-7 items-center">
            <li>
              <a class="font-extrabold text-white" href="">Home</a>
            </li>
            <li>
              <a class="font-extrabold text-white" href="">Services</a>
            </li>
            <li>
              <a class="font-extrabold text-white" href="">Projects</a>
            </li>
            <li>
              <a class="font-extrabold text-white" href="">Team</a>
            </li>
          </ul>

          <!--Desktop button -->
          <button
            class="hidden sm:block rounded drop-shadow-lg text-white text-xs px-6 py-2 bg-orange-500 hover:bg-orange-800 transition duration-300"
          >
            Get in Touch
          </button>

          <!--Hamburger -->

          <button @click="toggleMenu" class="sm:hidden px-6 focus:outline-none">
            <svg
              class="w-6 h-6"
              fill="none"
              stroke="currentColor"
              viewBox="0 0 24 24"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M4 6h16M4 12h16M4 18h16"
              />
            </svg>
          </button>
        </div>
      </div>

      <!--Mobile view-->
      <transition
        enter-active-class="transition duration-300 ease-out"
        enter-from-class="translate-x-full opacity-0"
        enter-to-class="translate-x-0 opacity-100"
        leave-active-class="transition duration-300 ease-in"
        leave-from-class="translate-x-0 opacity-100"
        leave-to-class="translate-x-full opacity-0"
      >
        <div v-if="isOpen" class="fixed inset-0 z-50 flex sm:hidden">
          <!-- Backdrop -->
          <div
            class="absolute inset-0 bg-black/40 backdrop-blur-sm"
            @click="isOpen = false"
          ></div>

          <!-- Drawer -->
          <div
            class="relative ml-auto w-3/4 max-w-sm h-full bg-white shadow-xl p-6 flex flex-col"
          >
            <!-- Cancel button -->
            <button @click="isOpen = false" class="self-end text-2xl mb-6">
              ✕
            </button>

            <!-- Menu -->
            <ul class="flex flex-col gap-6 text-left">
              <li><a class="font-semibold text-lg" href="/">Home</a></li>
              <li><a @click="scrollToServices(); isOpen = false" class="font-semibold text-lg" href="#">Services</a></li>
              <li><a @click="scrollToProjects(); isOpen = false" class="font-semibold text-lg" href="#">Projects</a></li>
              <li><a class="font-semibold text-lg" href="#">Team</a></li>
              <li>
                <button
                  class="mt-4 rounded text-white text-sm py-3 px-6 bg-orange-500 hover:bg-orange-800 transition"
                >
                  Get in Touch
                </button>
              </li>
            </ul>
          </div>
        </div>
      </transition>
    </nav>

    <!-- Content -->
    <div
      class="relative z-10 max-w-7xl mx-auto h-full flex items-center px-6 sm:px-12 lg:px-20"
    >
      <div class="max-w-2xl">
        

        <!-- Main Heading -->
        <h1
          class="text-white text-5xl sm:text-6xl lg:text-7xl font-extrabold leading-tight mb-10"
        >
          Tola Amicable <br />
          NIG Ltd.
        </h1>

        <!-- Small Top Text -->
        <div class="flex items-center gap-4 mb-6">
          <span class="w-14 h-[2px] bg-orange-400"></span>
          <p class="text-lg text-white font-medium">
            Always at the cutting edge
          </p>
        </div>

        <!-- Buttons -->
        <div
          class="flex flex-col sm:flex-row items-start sm:items-center gap-6"
        >
          <!-- Primary Button -->
          <a
            href="#services"
            class="bg-orange-500 hover:bg-orange-900 drop-shadow-lg text-white font-bold px-10 py-4 rounded-full transition duration-300"
          >
            OUR SERVICES
          </a>

          <!-- Projects Container -->
          <div class="inline-flex items-center gap-4">
            <a href="#projects" class="flex items-center gap-4 group">
              <!-- Circle -->
              <div class="relative flex items-center justify-center w-20 h-20">
                <span
                  class="absolute w-20 h-20 rounded-full border-2 border-orange-500/40"
                ></span>

                <span
                  class="absolute w-14 h-14 rounded-full border-2 border-orange-500"
                ></span>

                <span
                  class="w-8 h-8 rounded-full bg-orange-500 block group-hover:scale-110 transition duration-300"
                ></span>
              </div>

              <!-- Text -->
              <span class="text-lg font-medium text-white whitespace-nowrap">
                Our Projects
              </span>
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
