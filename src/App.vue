<script setup>

</script>

<template>
  <header class="pt-20 pb-10">
    <h1 class="text-center text-4xl">
      Aspect Ratio Calculator
    </h1>
  </header>

  <main class="mt-10 mb-20">
    <div class="max-w-2xl mx-auto px-10 py-20 relative overflow-hidden z-10 bg-gray-900 rounded-lg
      shadow-md before:w-24 before:h-24 before:absolute before:bg-indigo-600 before:rounded-full
      before:-z-10 before:blur-2xl after:w-32 after:h-32 after:absolute after:bg-blue-400 after:rounded-full
      after:-z-10 after:blur-xl after:bottom-12 after:end-4 after:animate-pulse before:animate-pulse
      flex flex-col gap-16 justify-center items-center before:start-12 before:top-10"
      >

      <div class="flex items-center justify-between gap-4">
        <input type="number" title="Width" v-model="width" @change="calculate" min="1"
          class="bg-transparent text-center max-w-30 p-1 focus:outline-0 border-b-2 border-transparent
            text-2xl focus:border-white duration-200">
        <font-awesome-icon icon="fa-solid fa-x text-2xl" />
        <input type="number" title="Height" v-model="height" @change="calculate" min="1"
          class="bg-transparent text-center max-w-30 p-1 focus:outline-0 border-b-2 border-transparent
            text-2xl focus:border-white duration-200">
      </div>

      <div class="text-3xl font-semibold border-2 border-white rounded-lg px-4 py-2 min-w-40 text-center" title="Aspect Ratio">
        {{ ratio }}
      </div>
    </div>

  </main>

  <footer class="my-10 px-4">
    <div class="container mx-auto">
      <hr class="opacity-25 mb-8">
      <p class="text-center text-2xl">
        Copyright © 2025 All Rights Reserved -
        <a href="https://github.com/Mahmoud217TR" target="__blank"
          class="hover:text-blue-400 transition-colors duration-300">
          MahmoudTR
        </a>
      </p>
    </div>
  </footer>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      width: 1920,
      height: 1080,
    }
  },
  computed: {
    ratio() {
      return this.calculate();
    }
  },
  methods: {
    calculate() {
      let gcd = this.gcd(this.width, this.height);
      return `${this.width / gcd} : ${this.height / gcd}`;
    },
    gcd(firstNamber, secondNumber) {
      return secondNumber === 0 ? firstNamber : this.gcd(secondNumber, firstNamber % secondNumber);
    }
  },
  mounted() {
    this.calculate();
  }
}
</script>
