<template>
    <div>
       <CollectionListVendor :vendorData="vendorData"  @show="addVendor" @showEdit="editVendor" @delete="deleteVendor"/>   
       <CollectionAddVendor v-if="show && !showData" @addData="addData" />
       <CollectionEditVendor v-if="showData && !show" :editVendorData="VendorData"  @editData="editData" />
  </div>

</template>

<script setup lang="ts">
import {ref,onMounted} from "vue"

onMounted(()=>{
console.log("onmounted--->")
})
const show = ref(false)
const showData = ref(false)

const getOptions = {
  method: "GET",
  headers: {
      "Content-Type": "application/json",
      Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiZTk3YTIxZjM4ZDc4NDgwYjlhYjdhOTI0M2Q0NjViNzgiLCJkIjoiMTY4MDA5NyIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyODc4Mjd9.qFyxIJYJLihyxfui4QRMOLjJgwBr95z3N3lWRDz89ZU`,
  },
};

var vendorData = useAuthLazyFetch(
    "https://v1-orm-gharpe.mercury.infinity-api.net/api/vendors/?offset=0&limit=100&sort_column=id&sort_direction=desc",
  getOptions
);
console.log("vendorData--->",vendorData)

const addData = (data:object) => {
    console.log("data in main--->",data,data.name)
    const postOptions = {
      method: "POST",
    headers: {
      "Content-Type": "application/json",
      Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiZTk3YTIxZjM4ZDc4NDgwYjlhYjdhOTI0M2Q0NjViNzgiLCJkIjoiMTY4MDA5NyIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyODc4Mjd9.qFyxIJYJLihyxfui4QRMOLjJgwBr95z3N3lWRDz89ZU`,
    },
    body: {
      name: data.name,
      category: data.category,
      email: data.email,
      industry: data.industry,
      rating: 0,
     type: "Vendor",
      address: {
    street: "sample",
    city: "sample",
    state: "sampleone",
    country: "string",
    zip_code: "string"
  },
    website: "string",
    status: 1,
     profile_id: "101"
    },
  };

  const addVendorData =  useAuthLazyFetchPost(
    "https://v1-orm-gharpe.mercury.infinity-api.net/api/vendors/",
    postOptions
  );
  console.log("addVendorData0000---->",addVendorData)
}

const editData = (data:object) => {
    console.log("data in main--->",data,data.name)
    const editOptions = {
      method: "PUT",
    headers: {
      "Content-Type": "application/json",
      Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiZTk3YTIxZjM4ZDc4NDgwYjlhYjdhOTI0M2Q0NjViNzgiLCJkIjoiMTY4MDA5NyIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyODc4Mjd9.qFyxIJYJLihyxfui4QRMOLjJgwBr95z3N3lWRDz89ZU`,
    },
    body: {
      name: data.name,
      category: data.category,
      email: data.email,
      industry: data.industry,
      rating: 0,
     type: "Vendor",
      address: {
    street: "sample",
    city: "sample",
    state: "sampleone",
    country: "string",
    zip_code: "string"
  },
    website: "string",
    status: 1,
     profile_id: "101"
    },
  };

  const editVendorData =  useAuthLazyFetchPut(
    `https://v1-orm-gharpe.mercury.infinity-api.net/api/vendors/${data.uid}`,
    editOptions
  );
  console.log("addVendorData0000---->",editVendorData)
}

   const deleteVendor = (data:any) => {
   const deleteOptions = {
    method: "DELETE",
  headers: {
    "Content-Type": "application/json",
    Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiZTk3YTIxZjM4ZDc4NDgwYjlhYjdhOTI0M2Q0NjViNzgiLCJkIjoiMTY4MDA5NyIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyODc4Mjd9.qFyxIJYJLihyxfui4QRMOLjJgwBr95z3N3lWRDz89ZU`,
  },
}

const deleteTemplateData = useAuthLazyFetchDelete (
    `https://v1-orm-lib.mars.hipso.cc/email-templates/${data.uid}`,
deleteOptions
)
console.log("deleteTemplateData--->",deleteTemplateData)
    }

const addVendor = () => {
  console.log('addVendor--->', show.value)
  show.value = true
  console.log('addVendor 2 --->', show.value)
}
const editVendor = () => {
        showData.value = true
    // console.log("editVendor--->",data)
}
</script>