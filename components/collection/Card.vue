<template>
  <div class="py-5 flex-col space-y-6 md:px-56 py-23 sm:items-center px-2 flex gap-4 lg:gap-0">
    <div class="lg:w-full md:flex gap-4 text-gray-800 sm: flex">
      <div v-for="item in headers" :key="item.id" class="py-2 md:flex-1 md: grid-cols-4 gap-2 sm: w-full">
        <h3 class="text-base md:text-lg font-semibold text-gray-900">{{ item.name }}</h3>
      </div>
    </div>
    <div v-for="application in applications" :key="application.id"
      class="lg:w-full md:w-full sm:w-full bg-gray-100 relative shadow rounded-lg text-gray-800 hover:shadow-lg cursor-pointer flex pl-0 p-0"
    > 
      <div class="lg:flex py-2 justify-around sm: flex-1 md:grid-cols-4 sm: w-full grid-cols-4 gap-4 flex">
        <div class="flex-shrink-0">
          <img class="lg:h-12 w-12 md: h-8 md:w-8 rounded-lg" :src="application.logo" alt="" />
        </div>
        <div>
          <p class="lg:h-12 w-12 md:h-8 md:w-8 rounded-lg">
            <a :href="application.href" class="text-blue-700 underline">{{ application.company }}</a>
          </p>
        </div>
        <div>
          <p class="lg:h-12 w-12 md:h-8 md:w-8 rounded-lg">{{ application.category }}</p>
        </div>
        <div class="text-violet-700">
          {{ application.technologies }}
        </div>
        <div class="text-violet-700">
          {{ application.emails }}
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";

const headers = ref([
  {
    id: 1,
    name: "",
  },
  {
    id: 2,
    name: "COMPANY",
  },
  {
    id: 3,
    name: "CATEGORY",
  },
  {
    id: 4,
    name: "TECHNOLOGIES",
  },
  {
    id: 5,
    name: "EMAILS",
  },
]);

const applications = ref([
  {
    id: 1,
    logo:
      "https://www.shutterstock.com/image-vector/letter-s-sync-logo-design-260nw-500701153.jpg",
    href: "",
    company: "Stark.ai",
    category: "Technology",
    technologies: "17 technologies found",
    emails: "87 emails found",
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
  {
    id: 7,
    logo:
      'https://www.shutterstock.com/image-vector/letter-s-sync-logo-design-260nw-500701153.jpg',
    href: '',
    company: 'Stark.ai',
    category: 'Technology',
    technologies: '17 technologies found',
    emails: '87 emails found',
  },
  {
    id: 8,
    logo:
      'https://t4.ftcdn.net/jpg/01/00/76/57/360_F_100765796_hVO2AGkofuyqsiiPGd4rdEkjq1FaC11k.jpg',
    href: '',
    company: 'Kong.ai',
    category: 'Technology',
    technologies: '16 technologies found',
    emails: '124 emails found',
  },
  {
    id: 9,
    logo:
      'https://png.pngtree.com/png-vector/20210703/ourmid/pngtree-link-icon-and-vector-graphics-png-image_3554928.jpg',
    href: '',
    company: 'Sampleone.ai',
    category: 'Technology',
    technologies: '20 technologies found',
    emails: '35 emails found',
  },
  {
    id: 10,
    logo:
      'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcT57u59lOwUriVW6dZt9Wmg3FsN24_YjaiUxGaenErk27tyZ7WZZPSEf5OLLZQYnMFONeM&usqp=CAU',
    href: '',
    company: 'Sampletwo.ai',
    category: 'Technology',
    technologies: '87 technologies found',
    emails: ' 176 Emails found',
  },
  {
    id: 11,
    logo:
      'https://i.pinimg.com/236x/7c/07/e8/7c07e882088a59b256550f01ffe65fa2.jpg',
    href: '',
    company: 'Samplethree.ai',
    category: 'Technology',
    technologies: '45 technologies found',
    emails: '123 emails found',
  },
])
</script>