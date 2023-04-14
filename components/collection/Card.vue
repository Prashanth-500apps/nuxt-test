<template>
  <div
    class="overflow-hidden bg-white shadow ml-[9.3rem] mt-[8.5rem] sm:rounded-md"
  >
    <ul role="list" class="divide-y divide-gray-200">
      <div class="flex justify-around">
        <p class="font-semibold ml-[16.4rem] text-lg">{{ company }}</p>
        <p class="font-semibold ml-[-12.8rem] text-lg">{{ category }}</p>
        <p class="font-semibold ml-[-6.8rem] text-lg">{{ technologies }}</p>
        <p class="py-3.5 pl-4 pr-3 text-center font-semibold text-gray sm:pl-0 text-lg">{{ emails }}</p>
      </div>
      <li v-for="application in applications" :key="application.id">
          <div class="flex px-4 py-4 sm:px-6 justify-around min-w-0 flex-1 grid-cols-4 gap-4">
            <div class="flex-shrink-0">
              <img
                class="h-12 w-12 rounded-full"
                :src="application.logo"
                alt=""
              />
            </div>
            <div class="flex min-w-0 ml-[-6.8rem]">
              <p class="h-12 w-12 rounded-full">
                <a :href="application.href" class="text-blue-700 underline">
                  {{ application.company }}
                </a>
              </p>
            </div>
            <div class="flex min-w-0 ml-[-8.8rem]">
              <p class="h-12 w-12 rounded-full">{{ application.category }}</p>
            </div>
            <div class="min-w-0 text-violet-700">
              {{ application.technologies }}
            </div>
            <div class="min-w-0 text-violet-700">
              {{ application.emails }}
            </div>
          </div>
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const company = ref('COMPANY')
const category = ref('CATEGORY')
const technologies = ref('TECHNOLOGIES')
const emails = ref('EMAILS')

const applications = ref([
  {
    id: 1,
    logo:
      'https://www.shutterstock.com/image-vector/letter-s-sync-logo-design-260nw-500701153.jpg',
    href: '',
    company: 'Stark.ai',
    category: 'Technology',
    technologies: '17 technologies found',
    emails: '87 emails found',
  },
  {
    id: 2,
    logo:
      'https://t4.ftcdn.net/jpg/01/00/76/57/360_F_100765796_hVO2AGkofuyqsiiPGd4rdEkjq1FaC11k.jpg',
    href: '',
    company: 'Kong.ai',
    category: 'Technology',
    technologies: '16 technologies found',
    emails: '124 emails found',
  },
  {
    id: 3,
    logo:
      'https://png.pngtree.com/png-vector/20210703/ourmid/pngtree-link-icon-and-vector-graphics-png-image_3554928.jpg',
    href: '',
    company: 'Sampleone.ai',
    category: 'Technology',
    technologies: '20 technologies found',
    emails: '35 emails found',
  },
  {
    id: 4,
    logo:
      'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcT57u59lOwUriVW6dZt9Wmg3FsN24_YjaiUxGaenErk27tyZ7WZZPSEf5OLLZQYnMFONeM&usqp=CAU',
    href: '',
    company: 'Sampletwo.ai',
    category: 'Technology',
    technologies: '87 technologies found',
    emails: ' 176 Emails found',
  },
  {
    id: 5,
    logo:
      'https://i.pinimg.com/236x/7c/07/e8/7c07e882088a59b256550f01ffe65fa2.jpg',
    href: '',
    company: 'Samplethree.ai',
    category: 'Technology',
    technologies: '45 technologies found',
    emails: '123 emails found',
  },
  {
    id: 6,
    logo:
      'https://cdn.vectorstock.com/i/preview-1x/74/95/chain-letter-s-link-logo-vector-46627495.webp',
    href: '',
    company: 'Samplefour.ai',
    category: 'Technology',
    technologies: '67 technologies found',
    emails: '56 emails found',
  },
])
</script>
