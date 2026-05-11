<script setup>
// import Navbar from "../components/Navbar.vue";
import Footer from "../components/Footer.vue";
import logo from "../assets/logo/logo.png";

const testimonials = [
  {
    name: "Sarah Johnson",
    role: "Project Manager",
    image: "https://i.pravatar.cc/150?img=12",
    text: "Maveric delivered exceptional results on our infrastructure project. Professional and highly reliable.",
  },
  {
    name: "Michael Lee",
    role: "Site Engineer",
    image: "https://i.pravatar.cc/150?img=15",
    text: "Their engineering expertise exceeded our expectations throughout the entire project.",
  },
  {
    name: "David Smith",
    role: "Construction Lead",
    image: "https://i.pravatar.cc/150?img=18",
    text: "Outstanding communication and execution. We would gladly work with Maveric again.",
  },
  {
    name: "Emma Wilson",
    role: "Operations Manager",
    image: "https://i.pravatar.cc/150?img=22",
    text: "Very smooth collaboration from start to finish with excellent attention to detail.",
  },
];

const duplicatedTestimonials = [...testimonials, ...testimonials];
</script>

<template>
  <!-- Hero Section comeback to this styling for mobile -->
  <section class="relative h-screen w-full overflow-hidden">
    <video
      autoplay
      muted
      loop
      playsinline
      class="absolute inset-0 w-full h-full object-cover"
    >
      <source src="../assets/videos/construction.bg.mp4" type="video/mp4" />
    </video>

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
              <li><a class="font-semibold text-lg" href="#">About</a></li>
              <li><a class="font-semibold text-lg" href="#">Services</a></li>
              <li><a class="font-semibold text-lg" href="#">Prices</a></li>
              <li>
                <button
                  class="mt-4 rounded text-white text-sm py-3 px-6 bg-lime-600 hover:bg-lime-800 transition"
                >
                  Get started
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
        <!-- Small Top Text -->
        <div class="flex items-center gap-4 mb-6">
          <span class="w-14 h-[2px] bg-orange-400"></span>
          <p class="text-lg text-black font-medium">
            Always at the cutting edge
          </p>
        </div>

        <!-- Main Heading -->
        <h1
          class="text-white text-5xl sm:text-6xl lg:text-7xl font-extrabold leading-tight mb-10"
        >
          Tolaamicable <br />
          NIG Ltd.
        </h1>

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
          <div class=" inline-flex items-center gap-4">
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

  <!-- Testimonials -->
  <section class="w-full bg-gray-100 py-20 border-t border-gray-200">
    <div class="max-w-7xl mx-auto px-6 sm:px-12 lg:px-20">
      <!-- Header -->
      <div class="mb-12">
        <p class="text-orange-500 font-semibold text-lg mb-4">Testimonials</p>

        <h2
          class="text-3xl sm:text-3xl lg:text-4xl font-bold text-gray-800 leading-tight"
        >
          What Our Clients <br />
          Say About Us
        </h2>
      </div>

      <!-- Cards -->
      <div class="overflow-hidden w-full py-4">
        <div class="flex animate-scroll gap-6 w-max">
          <!-- First Set -->
          <v-card
            v-for="(item, index) in duplicatedTestimonials"
            :key="index"
            elevation="0"
            class="rounded-3xl px-5 py-4 border border-gray-200 bg-white w-[320px] flex-shrink-0"
          >
            <!-- User -->
            <div class="flex items-center mb-3">
              <v-avatar size="45">
                <v-img :src="item.image" cover />
              </v-avatar>

              <div class="ml-3">
                <h3 class="text-base font-bold text-gray-800">
                  {{ item.name }}
                </h3>

                <p class="text-sm text-gray-500 mb-0">
                  {{ item.role }}
                </p>
              </div>
            </div>

            <!-- Stars -->
            <div class="flex items-center mb-3">
              <v-icon
                v-for="n in 5"
                :key="n"
                size="16"
                color="amber"
                class="mr-1"
              >
                mdi-star
              </v-icon>
            </div>

            <!-- Text -->
            <p class="text-gray-600 text-sm leading-relaxed">
              {{ item.text }}
            </p>
          </v-card>
        </div>
      </div>
    </div>
  </section>

  <!-- About Us Section -->
  <section class="w-full bg-gray-100 py-20 border-t border-gray-200">
    <div class="max-w-7xl mx-auto px-6 sm:px-12 lg:px-20">
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-16 items-start">
        <!-- Left Content -->
        <div>
          <!-- Small Heading -->
          <p class="text-orange-500 font-semibold text-lg mb-6">
            About Tolaamicable Contractors
          </p>

          <!-- Main Heading -->
          <h2
            class="text-3xl sm:text-3xl lg:text-4xl font-bold text-gray-800 leading-tight"
          >
            Tolaamicable - NIG LTD <br />
            Engineering meets Cutting <br />
            Edge Technology
          </h2>
        </div>

        <!-- Right Content -->
        <div class="flex flex-col justify-start">
          <!-- Paragraph -->
          <p class="text-gray-600 text-lg leading-relaxed mb-10 max-w-2xl">
            Specializing in Heavy Civil Engineering and Infrastructure Projects,
            Tolaamicable is headquartered in Lagos, with a presence across
            Nigeria. Over 25 years of engineering experience enables
            Tolaamicable to maintain absolute commitment to providing each
            client with an impressive return on investment for even the most
            complex earthwork and engineering challenges.
          </p>

          <!-- Button -->
          <a
            href="#about"
            class="inline-block bg-orange-500 hover:bg-orange-900 text-white font-bold text-sm px-10 py-4 rounded-full transition duration-300 w-fit"
          >
            MORE ABOUT US
          </a>
        </div>
      </div>
    </div>
  </section>

  <!-- Services Section -->
  <section class="w-full bg-gray-100 py-24">
    <div class="max-w-7xl mx-auto px-6 sm:px-12 lg:px-20">
      <!-- Header -->
      <div
        class="flex flex-col lg:flex-row justify-between items-start lg:items-center mb-16"
      >
        <!-- Left -->
        <div>
          <p class="text-orange-500 font-semibold text-lg mb-4">Our services</p>
          <h2
            class="text-4xl sm:text-5xl font-extrabold text-gray-900 leading-tight"
          >
            A comprehensive set <br />
            of services
          </h2>
        </div>

        <!-- Navigation Buttons -->
        <!-- <div class="flex gap-4 mt-8 lg:mt-0">
          <button
            class="w-14 h-14 border border-gray-400 flex items-center justify-center hover:bg-orange-500 hover:text-white transition"
          >
            &#8592;
          </button>
          <button
            class="w-14 h-14 border border-gray-400 flex items-center justify-center hover:bg-orange-500 hover:text-white transition"
          >
            &#8594;
          </button>
        </div> -->
      </div>

      <!-- Service Cards -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
        <!-- Card 1 -->
        <div
          class="bg-white shadow-sm hover:shadow-lg transition group border-b-4 border-orange-500"
        >
          <img
            src="../assets/img/archi.jpg"
            alt="Project Planning"
            class="w-full h-72 object-cover"
          />

          <div class="p-8 relative">
            <!-- Icon -->
            <div
              class="absolute -top-8 left-8 w-14 h-14 bg-orange-500 flex items-center justify-center text-white text-2xl"
            >
              <v-icon size="30">mdi-account-hard-hat-outline</v-icon>
            </div>

            <h3 class="text-2xl font-bold text-gray-900 mb-4 mt-6">
              Architectural Designs
            </h3>

            <p class="text-gray-600 leading-relaxed mb-6">
              Comprehensive architectural design solutions crafted to transform
              concepts into functional, modern, and visually striking spaces
              with precision and creativity.
            </p>

            <a
              href="#"
              class="text-orange-500 font-semibold underline hover:text-orange-600"
            >
              View service
            </a>
          </div>
        </div>

        <!-- Card 2 -->
        <div
          class="bg-white shadow-sm hover:shadow-lg transition group border-b-4 border-orange-500"
        >
          <img
            src="../assets/img/contractor-1.jpg"
            alt="Project Planning"
            class="w-full h-72 object-cover"
          />

          <div class="p-8 relative">
            <!-- Icon -->
            <div
              class="absolute -top-8 left-8 w-14 h-14 bg-orange-500 flex items-center justify-center text-white text-2xl"
            >
              ☰
            </div>

            <h3 class="text-2xl font-bold text-gray-900 mb-4 mt-6">
              Project Planning
            </h3>

            <p class="text-gray-600 leading-relaxed mb-6">
              Comprehensive planning solutions designed to ensure your projects
              are delivered efficiently, on budget, and with precision.
            </p>

            <a
              href="#"
              class="text-orange-500 font-semibold underline hover:text-orange-600"
            >
              View service
            </a>
          </div>
        </div>

        <!-- Card 3 -->
        <div
          class="bg-white shadow-sm hover:shadow-lg transition group border-b-4 border-orange-500"
        >
          <img
            src="../assets/img/contractor-3.jpg"
            alt="General Contracting"
            class="w-full h-72 object-cover"
          />

          <div class="p-8 relative">
            <div
              class="absolute -top-8 left-8 w-14 h-14 bg-orange-500 flex items-center justify-center text-white text-2xl"
            >
              <v-icon size="30">mdi-office-building</v-icon>
            </div>

            <h3 class="text-2xl font-bold text-gray-900 mb-4 mt-6">
              General Contracting
            </h3>

            <p class="text-gray-600 leading-relaxed mb-6">
              Delivering robust construction and infrastructure services with
              cutting-edge expertise and long-term reliability.
            </p>

            <a
              href="#"
              class="text-orange-500 font-semibold underline hover:text-orange-600"
            >
              View service
            </a>
          </div>
        </div>

        <!-- Card 4 -->
        <div
          class="bg-white shadow-sm hover:shadow-lg transition group border-b-4 border-orange-500"
        >
          <img
            src="../assets/img/contractor-2.jpg"
            alt="Project Management"
            class="w-full h-72 object-cover"
          />

          <div class="p-8 relative">
            <div
              class="absolute -top-8 left-8 w-14 h-14 bg-orange-500 flex items-center justify-center text-white text-2xl"
            >
              ⚙
            </div>

            <h3 class="text-2xl font-bold text-gray-900 mb-4 mt-6">
              Project Management
            </h3>

            <p class="text-gray-600 leading-relaxed mb-6">
              Expert coordination and oversight from conception to completion,
              ensuring seamless execution of every project phase.
            </p>

            <a
              href="#"
              class="text-orange-500 font-semibold underline hover:text-orange-600"
            >
              View service
            </a>
          </div>
        </div>
      </div>

      <!-- Bottom Buttons -->
      <!-- <div class="flex flex-col sm:flex-row gap-6 justify-center mt-16">
        

        <a
          href="#services"
          class="border border-gray-500 hover:bg-gray-900 hover:text-white text-gray-900 font-semibold px-10 py-4 transition"
        >
          Browse services
        </a>
      </div> -->
    </div>
  </section>

  <!-- Projects Section -->
  <section class="w-full bg-gray-100 py-24">
    <div class="max-w-7xl mx-auto px-6 sm:px-12 lg:px-20">
      <!-- Header -->
      <div
        class="flex flex-col lg:flex-row justify-between items-start lg:items-center mb-16"
      >
        <div>
          <p class="text-orange-500 font-semibold text-lg mb-4">
            Past Projects
          </p>
          <h2
            class="text-4xl sm:text-5xl font-extrabold text-gray-900 leading-tight"
          >
            Our project results <br />
            speak for themselves
          </h2>
        </div>

        <div class="flex gap-4 mt-8 lg:mt-0">
          <button
            class="bg-orange-500 text-white px-8 py-4 font-semibold hover:bg-orange-600 transition"
          >
            Get a quote
          </button>
          <button
            class="border border-gray-500 px-8 py-4 font-semibold text-gray-900 hover:bg-gray-900 hover:text-white transition"
          >
            Browse services
          </button>
        </div>
      </div>

      <!-- Projects Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-2 gap-8">
        <!-- Card 1 -->
        <div
          class="bg-white shadow-sm hover:shadow-lg transition group border-b-4 border-orange-500"
        >
          <img
            src="../assets/img/jendol.png"
            class="w-full h-72 object-cover"
          />

          <div class="p-8">
            <h3 class="text-2xl font-bold text-gray-900 mb-4">
              Mega Supermarket Construction in Ajah, Lagos
            </h3>

            <p class="text-gray-600 leading-relaxed mb-6">
              Modern retail infrastructure built with precision, durability, and
              contemporary architectural standards.
            </p>

            <div
              class="flex items-center justify-between text-sm text-gray-500 border-t pt-4"
            >
              <span class="flex items-center gap-2">🧱 Construction</span>
              <span class="flex items-center gap-2">📅 Sep 2021</span>
            </div>
          </div>
        </div>

        <!-- Card 2 -->
        <div
          class="bg-white shadow-sm hover:shadow-lg transition group border-b-4 border-orange-500"
        >
          <img
            src="https://images.unsplash.com/photo-1600607687939-ce8a6c25118c"
            class="w-full h-72 object-cover"
          />

          <div class="p-8">
            <h3 class="text-2xl font-bold text-gray-900 mb-4">
              Kitchen remodeling in Hollywood Hills, CA
            </h3>

            <p class="text-gray-600 leading-relaxed mb-6">
              Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nec ut
              viverra eros euismod.
            </p>

            <div
              class="flex items-center justify-between text-sm text-gray-500 border-t pt-4"
            >
              <span class="flex items-center gap-2">🧱 Remodeling</span>
              <span class="flex items-center gap-2">📅 Sep 2021</span>
            </div>
          </div>
        </div>
      </div>

      <!-- Bottom Buttons (same pattern as services) -->
      <div class="flex flex-col sm:flex-row gap-6 justify-center mt-16">
        <a
          href="#quote"
          class="bg-orange-500 hover:bg-orange-600 text-white font-bold px-10 py-4 transition"
        >
          Get a quote
        </a>

        <a
          href="#services"
          class="border border-gray-500 hover:bg-gray-900 hover:text-white text-gray-900 font-semibold px-10 py-4 transition"
        >
          Browse services
        </a>
      </div>
    </div>
  </section>

  <Footer />
</template>

<style scoped>
.animate-scroll {
  animation: scroll 25s linear infinite;
}

@keyframes scroll {
  from {
    transform: translateX(0);
  }

  to {
    transform: translateX(-50%);
  }
}
</style>
