<template>
  <div class="bg-white">
    <header class="absolute inset-x-0 top-0 z-50">
      <nav
        class="flex items-center justify-between p-6 lg:px-8"
        aria-label="Global"
      >
        <div class="flex lg:flex-1">
          <a href="#" class="-m-1.5 p-1.5">
            <div class="flex lg:flex-1">
              <img
                class="h-12 w-auto"
                src="https://sign.cc/images/logo.svg?v=1680522859104083589"
                alt=""
              />
            </div>
          </a>
        </div>
        <div class="hidden lg:flex ml-[69.4rem] lg:gap-x-12">
          <a
            v-for="item in navigation"
            :key="item.name"
            :href="item.href"
            class="text-sm font-semibold leading-6 text-gray-900"
          >
            {{ item.name }}
          </a>
        </div>
        <div class="hidden lg:flex lg:flex-1 lg:justify-end">
          <a href="#" class="text-sm font-semibold leading-6 text-gray-900">
            Sign Up
            <span aria-hidden="true">&rarr;</span>
          </a>
        </div>
      </nav>
      <Dialog
        as="div"
        class="lg:hidden"
        @close="mobileMenuOpen = false"
        :open="mobileMenuOpen"
      >
        <div class="fixed inset-0 z-50" />
        <DialogPanel
          class="fixed inset-y-0 right-0 z-50 w-full overflow-y-auto bg-white px-6 py-6 sm:max-w-sm sm:ring-1 sm:ring-gray-900/10"
        >
          <div class="flex items-center justify-between">
            <a href="#" class="-m-1.5 p-1.5">
              <span class="sr-only">Your Company</span>
              <img
                class="h-8 w-auto"
                src="https://tailwindui.com/img/logos/mark.svg?color=indigo&shade=600"
                alt=""
              />
            </a>
            <button
              type="button"
              class="-m-2.5 rounded-md p-2.5 text-gray-700"
              @click="mobileMenuOpen = false"
            >
              <span class="sr-only">Close menu</span>
              <XMarkIcon class="h-6 w-6" aria-hidden="true" />
            </button>
          </div>
          <div class="mt-6 flow-root">
            <div class="-my-6 divide-y divide-gray-500/10">
              <div class="space-y-2 ml-[69.6rem] py-2">
                <a
                  v-for="item in navigation"
                  :key="item.name"
                  :href="item.href"
                  class="-mx-3 block rounded-lg px-3 py-2 text-base font-semibold leading-7 text-gray-900 hover:bg-gray-50"
                >
                  {{ item.name }}
                </a>
              </div>
              <div class="py-6">
                <a
                  href="#"
                  class="-mx-3 block rounded-lg px-3 py-2.5 text-base font-semibold leading-7 text-gray-900 hover:bg-gray-50"
                >
                  Log in
                </a>
              </div>
            </div>
          </div>
        </DialogPanel>
      </Dialog>
    </header>
    <div class="relative isolate px-6 pt-14 lg:px-8">
      <div
        class="absolute inset-x-0 -top-40 -z-10 transform-gpu overflow-hidden blur-3xl sm:-top-80"
        aria-hidden="true"
      >
        <div
          class="relative left-[calc(50%-11rem)] aspect-[1155/678] w-[36.125rem] -translate-x-1/2 rotate-[30deg] bg-gradient-to-tr from-[#ff80b5] to-[#9089fc] opacity-30 sm:left-[calc(50%-30rem)] sm:w-[72.1875rem]"
          style="
            clip-path: polygon(
              74.1% 44.1%,
              100% 61.6%,
              97.5% 26.9%,
              85.5% 0.1%,
              80.7% 2%,
              72.5% 32.5%,
              60.2% 62.4%,
              52.4% 68.1%,
              47.5% 58.3%,
              45.2% 34.5%,
              27.5% 76.7%,
              0.1% 64.9%,
              17.9% 100%,
              27.6% 76.8%,
              76.1% 97.7%,
              74.1% 44.1%
            );
          "
        />
      </div>
      <div class="mx-auto ml-34px max-w-2xl py-32 sm:py-48 lg:py-56">
        <div class="text-center ml-[-31.8rem] mt-[-6.8rem]">
          <h1
            class="text-4xl font-bold tracking-tight text-gray-900 sm:text-6xl"
          >
            Best Electronic Signature
          </h1>
          <h3
            class="text-3xl mt-3 font-bold tracking-tight text-gray-900 sm:text-1xl"
          >
            <CheckIcon
              class="absolute ml-[17.2rem] mt-[4.5rem] h-5 w-5 text-green-600"
              aria-hidden="true"
            />
            Join the SaaS Revolution - 50 Apps for ₹999
          </h3>
          <p class="mt-6 text-lg leading-8 text-gray-600">
            <CheckIcon
              class="absolute ml-[20.2rem] mt-[3.7rem] h-5 w-5 text-green-600"
              aria-hidden="true"
            />
            Sign documents and request electronic signatures quickly and
            securely
          </p>
          <p class="mt-6 text-lg leading-8 text-gray-600">
            <CheckIcon
              class="absolute ml-[17.2rem] mt-[4.0rem] h-5 w-5 text-green-600"
              aria-hidden="true"
            />
            Choose who needs to sign (“Me”, “Me and Others”, “Others”)
          </p>
          <p class="mt-6 text-lg leading-8 text-gray-600">
            <CheckIcon
              class="absolute ml-[16.5rem] mt-[4.2rem] h-5 w-5 text-green-600"
              aria-hidden="true"
            />
            Streamline your workflow and close deals faster with CRM integration
          </p>
          <p class="mt-6 text-lg leading-8 text-gray-600">
            <CheckIcon
              class="absolute ml-[17.2rem] mt-[4.1rem] h-5 w-5 text-green-600"
              aria-hidden="true"
            />
            Store and manage documents in Dropbox, Google Drive, Box, and
            OneDrive
          </p>
          <p class="mt-6 text-lg leading-8 text-gray-600">
            Create signing order and track sign requests with utmost convenience
          </p>
          <div class="mt-10 flex items-center justify-center gap-x-6">
            <button
              type="button"
              class="rounded-md w-200 bg-indigo-600 px-3.5 py-2.5 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
            >
              Sign Up
            </button>
            or
            <div class="flex items-center space-x-2">
              <div class="flex flex-shrink-0 -space-x-1">
                <img
                  v-for="member in members"
                  :key="member.imageUrl"
                  class="h-6 w-6 max-w-none rounded-full ring-2 ring-white"
                  :src="member.imageUrl"
                  :alt="member.name"
                />
              </div>
            </div>
          </div>
        </div>
        <div class="ml-[29.3rem] mt-[-36.8rem] mx-auto px-6 py-32 sm:py-40">
          <object
            data="https://sign.cc/images/electronic-signature.svg?v=1680522859104083589"
          />
        </div>
        <div
          class="absolute inset-x-0 bottom-0 -z-10 h-24 bg-gradient-to-t from-white sm:h-32"
        />
      </div>
      <div
        class="absolute inset-x-0 top-[calc(100%-13rem)] -z-10 transform-gpu overflow-hidden blur-3xl sm:top-[calc(100%-30rem)]"
        aria-hidden="true"
      >
        <div
          class="relative left-[calc(50%+3rem)] aspect-[1155/678] w-[36.125rem] -translate-x-1/2 bg-gradient-to-tr from-[#ff80b5] to-[#9089fc] opacity-30 sm:left-[calc(50%+36rem)] sm:w-[72.1875rem]"
          style="
            clip-path: polygon(
              74.1% 44.1%,
              100% 61.6%,
              97.5% 26.9%,
              85.5% 0.1%,
              80.7% 2%,
              72.5% 32.5%,
              60.2% 62.4%,
              52.4% 68.1%,
              47.5% 58.3%,
              45.2% 34.5%,
              27.5% 76.7%,
              0.1% 64.9%,
              17.9% 100%,
              27.6% 76.8%,
              76.1% 97.7%,
              74.1% 44.1%
            );
          "
        />
      </div>
    </div>
    <div class="mt-[-7.8rem]">
      <CollectionInfo />
    </div>
    <div class="mt-[-7.8rem]">
      <CollectionInfoTwo />
    </div>
    <div class="mt-[-7.8rem]">
      <CollectionPrice />
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import {
  Dialog,
  DialogPanel,
  MenuItems,
  Menu,
  MenuButton,
} from '@headlessui/vue'
import {
  Bars3Icon,
  XMarkIcon,
  ChevronUpDownIcon,
  CheckIcon,
} from '@heroicons/vue/24/outline'

const navigation = [
  { name: 'Features', href: '#' },
  { name: 'Prices', href: '#' },
  { name: 'Resource', href: '#' },
  { name: 'Login', href: '#' },
]

const members = [
  {
    imageUrl:
      'https://img.freepik.com/free-psd/google-icon-isolated-3d-render-illustration_47987-9777.jpg?w=2000',
  },
  {
    imageUrl:
      'https://sign.cc/lib/images/sso-icons/linkedin.svg?v=1680522859104083589',
  },
  {
    imageUrl:
      'https://sign.cc/lib/images/sso-icons/microsoft.svg?v=1680522859104083589',
  },
  {
    imageUrl:
      'https://sign.cc/lib/images/sso-icons/facebook.svg?v=1680522859104083589',
  },
]

const mobileMenuOpen = ref(false)
</script>
