<template>
  <div class="px-4 sm:px-6 lg:px-8">
    <div class="mt-8 flow-root">
      <div class="-mx-4 -my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
        <div class="inline-block min-w-full py-2 align-middle sm:px-6 lg:px-8">
          <div class="sm:flex sm:items-center">
            <div class="mt-4 sm:ml-1 sm:mt-0 sm:flex-none">
              <button
                type="button"
                class="block rounded-md bg-indigo-600 px-3 py-2 text-center text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
                @click="emits('openSlideout', true)"
              >
                Add Contact
              </button>
            </div>
            <div class="ml-9">
              <label> Search Student : </label>
              <input
                v-model="search"
                type="text"
                @input="handleInput(search)"
                placeholder="Please search by Name"
              />
            </div>
          </div>
          <table class="min-w-full divide-y divide-gray-300">
            <thead>
              <tr>
                <th
                  scope="col"
                  class="py-3.5 pl-4 pr-3 text-left text-sm font-semibold text-gray-900 sm:pl-0"
                >
                  Sr.No
                </th>
                <th
                  scope="col"
                  class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900"
                >
                  Name
                </th>
                <th
                  scope="col"
                  class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900"
                >
                  Age
                </th>
                <th
                  scope="col"
                  class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900"
                >
                  Gender
                </th>
                <th
                  scope="col"
                  class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900"
                >
                  Date of Birth
                </th>
                <th
                  scope="col"
                  class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900"
                >
                  Education
                </th>
              </tr>
            </thead>
            <tbody class="divide-y divide-gray-200">
              <tr v-for="(user, index) in formData" :key="index">
                <td
                  class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-0"
                >
                  {{ user.srNo }}
                </td>
                <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">
                  {{ user.name }}
                </td>
                <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">
                  {{ user.age }}
                </td>
                <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">
                  {{ user.gender }}
                </td>
                <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">
                  {{ user.dob }}
                </td>
                <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">
                  {{ user.education }}
                </td>
                <td
                  class="relative whitespace-nowrap py-4 pl-3 pr-4 text-right text-sm font-medium sm:pr-0"
                >
                  <button
                    href="#"
                    class="text-indigo-600 hover:text-indigo-900 mr-4"
                    @click="emits('editSlideout', user)"
                  >
                    <PencilSquareIcon class="h-6 w-6" aria-hidden="true" />
                  </button>
                  <button
                    href="#"
                    class="text-indigo-600 hover:text-indigo-900 mr-4"
                    @click="open = true"
                  >
                    <TrashIcon class="h-6 w-6" aria-hidden="true" />
                  </button>
                </td>
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
                            <div class="sm:flex sm:items-start">
                              <div
                                class="mx-auto flex h-12 w-12 flex-shrink-0 items-center justify-center rounded-full bg-red-100 sm:mx-0 sm:h-10 sm:w-10"
                              >
                                <ExclamationTriangleIcon
                                  class="h-6 w-6 text-red-600"
                                  aria-hidden="true"
                                />
                              </div>
                              <div
                                class="mt-3 text-center sm:ml-4 sm:mt-0 sm:text-left"
                              >
                                <DialogTitle
                                  as="h3"
                                  class="text-base font-semibold leading-6 text-gray-900"
                                >
                                  Are you sure ?
                                </DialogTitle>
                                <div class="mt-2">
                                  <p class="text-sm text-gray-500">
                                    Deleting will permanently remove. This
                                    cannot be undone.
                                  </p>
                                </div>
                              </div>
                            </div>
                            <div class="mt-5 sm:ml-10 sm:mt-4 sm:flex sm:pl-4">
                              <button
                                type="button"
                                class="inline-flex w-full justify-center rounded-md bg-red-600 px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-red-500 sm:w-auto"
                                @click="
                                  emits('deleteItem', user, index),
                                    (open = false)
                                "
                              >
                                Delete
                              </button>
                              <button
                                type="button"
                                class="mt-3 inline-flex w-full justify-center rounded-md bg-white px-3 py-2 text-sm font-semibold text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 hover:bg-gray-50 sm:ml-3 sm:mt-0 sm:w-auto"
                                @click="open = false"
                                ref="cancelButtonRef"
                              >
                                Cancel
                              </button>
                            </div>
                          </DialogPanel>
                        </TransitionChild>
                      </div>
                    </div>
                  </Dialog>
                </TransitionRoot>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
    <Bar :data="chartData" :options="chartOptions" />
  </div>
</template>

<script setup lang="ts">
import { PencilSquareIcon, TrashIcon } from "@heroicons/vue/24/outline";
import {
  Dialog,
  DialogPanel,
  DialogTitle,
  TransitionChild,
  TransitionRoot,
} from "@headlessui/vue";
import { Bar } from "vue-chartjs";
import {
  Chart as ChartJS,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale,
} from "chart.js";
import { ref, defineEmits, onMounted, defineProps } from "vue";
const emits = defineEmits(["openSlideout", "deleteItem"]);

let search = ref("");

ChartJS.register(CategoryScale, LinearScale, BarElement, Tooltip, Legend);

const props = defineProps({
  formData: Array,
});

onMounted(() => {
  console.log("labels---->", props.formData, Object.keys(props.formData));
});

const chartData = {
  labels: Object.keys(props.formData),
  datasets: [
    {
      data: Object.values(props.formData),
      backgroundColor: "rgba(20, 255, 0, 0.3)",
      borderColor: "rgba(100, 255, 0, 1)",
      borderWidth: 2,
    },
  ],
};
const handleInput = (data) => {
  console.log("handle--input--->", data);
  props.formData.find((item) => {
    console.log("item and data--->", item, data);
    if (item && item["name"] && item["name"].includes(data)) {
      console.log("inside includes---->", item);
    //   props.formData = item
      // localStorage.setItem("updateData",)
      // user.name = item.name
    }
  });
};
const chartOptions = {
  responsive: true,
};

let open = ref(false);
</script>
