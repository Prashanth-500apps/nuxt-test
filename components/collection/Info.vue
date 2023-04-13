<template>
  <div class="bg-white py-24 sm:py-32">
    <div class="mx-auto max-w-7xl px-6 lg:px-8">
      <div class="mx-auto max-w-2xl text-center">
        <h1 class="text-3xl font-bold tracking-tight text-gray-900 sm:text-4xl">
          Why Choose Sign.cc for Electronic Signature?
        </h1>
        <p class="mt-2 text-lg leading-8 text-gray-600">
          Top 10 reasons why your business should use Sign.cc and 50+ other apps
          from 500apps
        </p>
      </div>
      <div
        class="mx-auto  mt-16 grid max-w-2xl grid-cols-6 gap-x-8 gap-y-20 lg:mx-0 lg:max-w-none lg:grid-cols-5"
      >
        <article
          v-for="post in posts"
          :key="post.id"
          class="flex flex-col items-start justify-between"
        >
          <div class="relative">
            <div class="aspect-[16/9] rounded-2xl bg-indigo-200 object-cover">
              <h1>{{ post.title }}</h1>
              <p
                class="relative z-10 rounded-full bg-indigo-200 px-3 py-1.5 font-medium "
              >
                {{ post.description }}
              </p>
            </div>
          </div>
        </article>
      </div>
      <button
        type="button"
        class="rounded-md ml-[19.2rem] mt-[4.4rem] w-200 bg-indigo-600 px-3.5 py-2.5 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
      >
        Sign Up
      </button>
      <h2 class="rounded-md ml-[27.2rem] mt-[-1.8rem]"> Why Sign.cc? </h2>
    </div>
  </div>
</template>

<script setup>
const posts = [
  {
    id: 1,
    title: '#1',
    description:
      'Get digital signatures on documents like sales contracts, employee HR letters, and more',
  },
  {
    id: 2,
    title: '#2',
    description:
      'Create components like signature, date, initials on document via drag and drop builder',
  },
  {
    id: 3,
    title: '#3',
    description:
      'Enable multi-party signing and share documents to multiple users',
  },
  {
    id: 4,
    title: '#4',
    description: 'Choose from 15+ scenario based pre-designed templates',
  },
  {
    id: 5,
    title: '#5',
    description:
      'Upload documents from your local system or cloud providers like Dropbox, Google Drive and 500Box',
  },
  {
    id: 6,
    title: '#6',
    description: 'Track individual signee status for each document',
  },
  {
    id: 7,
    title: '#7',
    description:
      'Send documents for signature from your favorite CRM software like CRM.io',
  },
  {
    id: 8,
    title: '#8',
    description: 'Set a hierarchical order for signing documents',
  },
  {
    id: 9,
    title: '#9',
    description: 'Unbelievable pricing - the lowest you will ever find',
  },
  {
    id: 10,
    title: '#10',
    description:
      'Everything your business needs - 50 apps, 24/5 support and 99.95% uptime',
  },
]
</script>
