<template>
  <h1 class="mb-8 text-2xl">CSS Grid</h1>
  <div class="my-8 md:w-4/5 md:m-auto mx-4">
    <nav class="flex justify-between">
      <button class="bg-indigo-500 rounded-sm p-2 text-white text-xs md:text-base mx-2" @click="changeActiveExample('GridGaps')">Responsive & Grid Gaps</button>
      <button class="bg-indigo-500 rounded-sm p-2 text-white text-xs md:text-base mx-2" @click="changeActiveExample('ColumnStartEnd')">Column Start/End</button>
      <button class="bg-indigo-500 rounded-sm p-2 text-white text-xs md:text-base mx-2" @click="changeActiveExample('DomainHeader')">Domain Header Example</button>
      <button class="bg-indigo-500 rounded-sm p-2 text-white text-xs md:text-base mx-2" @click="changeActiveExample('FormExample')">Form Example</button>
      <!-- <button class="bg-indigo-500 rounded-sm p-2 text-white" @click="activeExample = 'form'">Form Example</button> -->
      <!-- <button></button>
      <button></button> -->
    </nav>
  </div>
  <h2 class="mt-4 mb-8" v-if="activeExample === 'GridGaps'">Responsive & Grid Gaps</h2 >
  <!-- hover:grid-cols-3  -->
  <div class="w-4/5 m-auto grid grid-cols-4 gap-4 md:grid-cols-8" v-if="activeExample === 'GridGaps'">
    <div class="h-12 bg-red-500"></div>
    <div class="h-12 bg-red-500"></div>
    <div class="h-12 bg-red-500"></div>
    <div class="h-12 bg-red-500"></div>
    <div class="h-12 bg-red-500"></div>
    <div class="h-12 bg-red-500"></div>
    <div class="h-12 bg-red-500"></div>
    <div class="h-12 bg-red-500"></div>
    <div class="h-12 bg-red-500"></div>
    <div class="h-12 bg-red-500"></div>
    <div class="h-12 bg-red-500"></div>
    <div class="h-12 bg-red-500"></div>
  </div>

  <h2 class="mt-4 mb-8" v-if="activeExample === 'ColumnStartEnd'">Column Start/End</h2>
  <div class="w-4/5 m-auto grid grid-cols-6 gap-4" v-if="activeExample === 'ColumnStartEnd'">
    <div
      class="
        h-12
        bg-red-500
        flex
        justify-center
        text-white
        items-center
        col-span-4
      "
    >
      Col span of 4
    </div>
    <div class="h-12 bg-red-500"></div>
    <div class="h-12 bg-red-500"></div>
    <div
      class="
        h-12
        bg-red-500
        flex
        justify-center
        text-white
        items-center
        col-start-3 col-end-6
      "
    >
      Start 3, end 6
    </div>
    <div class="h-12 bg-red-500"></div>
    <div class="h-12 bg-red-500"></div>
    <div class="h-12 bg-red-500"></div>
    <div class="h-12 bg-red-500"></div>
    <div class="h-12 bg-red-500"></div>
    <div
      class="
        h-12
        bg-red-500
        flex
        justify-center
        text-white
        items-center
        col-start-6
      "
    >
      Start 6
    </div>
    <div class="h-12 bg-red-500"></div>
    <div class="h-12 bg-red-500"></div>
  </div>



  <h2 class="mt-4 mb-8" v-if="activeExample === 'DomainHeader'">Example of where it can be useful</h2>
  <button
    class="bg-blue-500 w-32 h-12 rounded text-white mb-8"
    @click="changeLoaded"
    v-if="activeExample === 'DomainHeader'"
  >
    Loaded: {{ loaded }}
  </button>
  <div class="w-4/5 m-auto grid grid-cols-5 gap-4 mb-8" v-if="activeExample === 'DomainHeader'">
    <div class="gridCell statusIconHeader">Status Icon Header</div>
    <div class="gridCell domainHeader">Domain Name Header</div>
    <div class="gridCell statusIcon transition-all duration-200" v-if="loaded">
      Status Icon
    </div>
    <div class="gridCell domain">Domain Name</div>
    <div class="gridCell statusIcon">Status Icon</div>
    <div class="gridCell domain">Domain Name</div>
    <div class="gridCell statusIcon">Status Icon</div>
    <div class="gridCell domain" v-if="loaded">Domain Name</div>
    <div class="gridCell statusIcon">Status Icon</div>
    <div class="gridCell domain">Domain Name</div>
    <div class="gridCell statusIcon" v-if="loaded">Status Icon</div>
    <div class="gridCell domain">Domain Name</div>
  </div>

  <h2 class="mt-4 mb-8" v-if="activeExample === 'FormExample'">More Responsive Forms</h2>

  <div
    class="
      w-4/5
      m-auto
      grid grid-cols-1
      md:grid-cols-5
      gap-4
      mb-8
      bg-slate-50
      h-auto
      p-8
      items-center
    "
    v-if="activeExample === 'FormExample'"
  >
    <label for="name" class="col-span-2 h-12 flex items-center justify-center"
      >Enter Name</label
    >
    <input
      type="text"
      id="name"
      class="col-span-3 h-12 rounded-md border border-gray-500"
    />

    <label for="email" class="col-span-2 h-12 flex items-center justify-center"
      >Enter Email</label
    >
    <input
      type="text"
      id="email"
      class="col-span-3 h-12 rounded-md border border-gray-500"
    />
  </div>
</template>

<script>
export default {
  data() {
    return {
      loaded: true,
      activeExample: ''
    };
  },
  methods: {
    changeLoaded() {
      this.loaded = !this.loaded;
    },
    changeActiveExample(example) {
      this.activeExample = example
    }
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.gridCell {
  @apply h-12 bg-red-500 flex items-center justify-center text-white;
}

.domain {
  @apply col-start-3 col-span-2;
}

.statusIcon {
  @apply col-start-1;
}

.statusIconHeader {
  @apply col-start-1 col-span-2 bg-indigo-500;
}

.domainHeader {
  @apply col-span-3 bg-indigo-500;
}
</style>
