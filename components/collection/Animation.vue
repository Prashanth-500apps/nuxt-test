<template>
  <div class="bg-white py-24 sm:py-32">
    <div class="mx-auto max-w-7xl px-6 lg:px-8">
      <div class="mx-auto max-w-2xl lg:max-w-none">
        <dl
          class="mt-16 grid grid-cols-1 gap-0.5 overflow-hidden rounded-2xl text-center sm:grid-cols-2 lg:grid-cols-4"
        >
          <div
            v-for="stat in stats"
            :key="stat.id"
            class="flex flex-col bg-gray-400/5 p-8"
          >
            <dt class="text-sm font-semibold leading-6 text-gray-600">
              {{ stat.name }}
            </dt>
            <dd
              class="order-first text-3xl font-semibold tracking-tight text-gray-900"
            >
              {{ stat.value }}
            </dd>
          </div>
        </dl>
      </div>
      <div>
        <h2
          class="text-3xl ml-[12.2rem] mt-[2.2rem] font-bold tracking-tight text-gray-900 sm:text-4xl"
        >
          All-in-One infinity Suite with 50 Apps for Your Business
        </h2>
        <p class="mt-4 ml-[17.2rem] text-lg leading-8 text-gray-600">
          Everything you need for your Marketing, Sales, HR, Support,
          Developers, and more
        </p>
      </div>
    </div>
    <div >
      <object
        data="https://sign.cc/lib/images/suite-img/info-graphic-1.svg?v=1680522859104083589" class="w-[50%] ml-[24.3rem]"
      />
    </div>
  </div>
</template>

<script setup>
const stats = [
  { id: 1, name: 'Businesses', value: '91,436+' },
  { id: 2, name: 'Data Centers', value: '6' },
  { id: 3, name: 'Global Uptime', value: '99.9%' },
  { id: 4, name: 'Apps', value: '50' },
]
</script>
