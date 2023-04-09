<template>
  <div>
    <div>
      <CollectionVendorList
        :vendorInfo="vendorInfo"
        @show="addVendor"
        @showEdit="editVendor"
        @delete="deleteVendor"
      />
    </div>
    <div v-if="show">
      <CollectionVendorAdd v-if="show" @addData="addData" :key="renderAdd" />
    </div>
    <div v-if="showData">
      <CollectionVendorEdit
        v-if="showData"
        :editVendorData="VendorData"
        :editInfo="editInfo"
        @editData="editData"
        :key="renderEdit"
      />
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

// Declaring variables
const show = ref(false)
const showData = ref(false)
const renderEdit = ref(0)
const renderAdd = ref(0)
const editInfo = ref({})

// Open add vendor modal
const addVendor = (data) => {
  show.value = data
  renderAdd.value++
}

// Open the edit vendor modal
const editVendor = (data) => {
  showData.value = true
  renderEdit.value++
  editInfo.value = data
}

//Get all the vendors
var vendorData = useAuthLazyFetch(
  'https://v1-orm-gharpe.mercury.infinity-api.net/api/vendors/?offset=0&limit=100&sort_column=id&sort_direction=desc',
)

const vendorInfo = ref(vendorData.data._rawValue)

// Add vendor
const addData = async (body: object) => {
  const postOptions = {
    body: body,
  }
  await useAuthLazyFetchPost(
    'https://v1-orm-gharpe.mercury.infinity-api.net/api/vendors/',
    postOptions,
  )
  vendorInfo.value.unshift(body)
}

const editData = (body: object) => {
  console.log('data in main--->', body)
  const editOptions = {
    body: body,
  }
  // Updating the vendor based on uid
  const editVendorData = useAuthLazyFetchPut(
    `https://v1-orm-gharpe.mercury.infinity-api.net/api/vendors/${body.uid}`,
    editOptions,
  )
  console.log('addVendorData0000---->', editVendorData.value)
}

// deleting the vendor based on uid
const deleteVendor = async (data: any,index) => {
  await useAuthLazyFetchDelete(
    `https://v1-orm-gharpe.mercury.infinity-api.net/api/vendors/${data.uid}`,
  )
  console.log("data and index in delete--->",data,index)
  vendorInfo.value.splice(index,1)
}

</script>
