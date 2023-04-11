<template>
  <div>
    <TransitionRoot as="template" :show="open">
      <Dialog as="div" class="relative z-10" @close="open = false">
        <TransitionChild
          as="template"
          enter="ease-out duration-300"
          enter-from="opacity-0"
          enter-to="opacity-100"
          leave="ease-in duration-200"
          leave-from="opacity-100"
          leave-to="opacity-0"
        >
          <div
            class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity"
          />
        </TransitionChild>

        <div class="fixed inset-0 z-10 overflow-y-auto">
          <div
            class="flex min-h-full items-end justify-center p-4 text-center sm:items-center sm:p-0"
          >
            <TransitionChild
              as="template"
              enter="ease-out duration-300"
              enter-from="opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95"
              enter-to="opacity-100 translate-y-0 sm:scale-100"
              leave="ease-in duration-200"
              leave-from="opacity-100 translate-y-0 sm:scale-100"
              leave-to="opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95"
            >
              <DialogPanel
                class="relative transform overflow-hidden rounded-lg bg-white px-4 pb-4 pt-5 text-left shadow-xl transition-all sm:my-8 sm:w-full sm:max-w-lg sm:p-6"
              >
              <h1 class="text-4xl font-black text-gray-900 dark:text-white"> {{ header }} </h1>
                <div
                  class="bg-white flex flex-col h-full py-3.5 rounded-lg border"
                >
                  <div class="flex justify-center">
                    <label>Search Text :</label>
                    <input v-model="searchText" type="text" />
                  </div>
                  <div class="flex justify-center">
                    <Tree
                      :nodes="hierarchyData"
                      :search-text="searchText"
                      :use-checkbox="true"
                      :use-icon="false"
                      use-row-delete
                      show-child-count
                      @nodeExpanded="onNodeExpanded"
                      @update:nodes="onUpdate"
                      @nodeClick="onNodeClick"
                    />
                  </div>
                  <!-- </div>
                  </div> -->
                </div>
              </DialogPanel>
            </TransitionChild>
          </div>
        </div>
      </Dialog>
    </TransitionRoot>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import Tree from 'vue3-tree'
import 'vue3-tree/dist/style.css'
import {
  Dialog,
  DialogPanel,
  DialogTitle,
  TransitionChild,
  TransitionRoot,
} from '@headlessui/vue'

// Store hierarchy Data
const hierarchyData = ref([
  {
    id: 1,
    label: 'CEO',
    nodes: [
      {
        id: 2,
        label: 'Manager 1',
        nodes: [
          {
            id: 4,
            label: 'Product Owner 1',
            nodes: [
              {
                id: 5,
                label: 'Team Lead',
                nodes: [
                  {
                    id: 6,
                    label: 'Developer 1',
                  },
                  {
                    id: 7,
                    label: 'Developer 2',
                  },
                ],
              },
              {
                id: 8,
                label: 'Testing Lead',
                nodes: [
                  {
                    id: 9,
                    label: 'QA',
                  },
                ],
              },
            ],
          },
        ],
      },
      {
        id: 10,
        label: 'Manager 2',
        nodes: [
          {
            id: 11,
            label: 'Product Owner 2',
            nodes: [
              {
                id: 12,
                label: 'Team Lead',
                nodes: [
                  {
                    id: 13,
                    label: 'Developer 1',
                  },
                  {
                    id: 14,
                    label: 'Developer 2',
                  },
                ],
              },
              {
                id: 15,
                label: 'Testing Lead',
                nodes: [
                  {
                    id: 16,
                    label: 'QA',
                  },
                ],
              },
            ],
          },
        ],
      },
    ],
  },
  {
    id: 17,
    label: 'Grand Father',
  },
])

// Variables declarations
const searchText = ref('')
const open = ref(true)
const header = ref("Hierarchy Tree")

// When we expand or close the node below function will be called, If we expand node state will be true else it will be false
const onNodeExpanded = (data, state) => {
  console.log('state and data---->', state,data)
}

// If we delete any node using use-row-delete below function will be called
const onUpdate = (data) => {
  console.log('data in onUpdate---->', data)
}

// If we click on any particular node below function will be called
const onNodeClick = (data) => {
  console.log('data in onNodeClick--->', data)
}
</script>
