<template>
  <div>
    <div>
      <CollectionListProject :projectsData="projectsData" @showAdd="showAdd" @showEdit="showEdit" @deleteProject="deleteProject" />
    </div>
    <div v-if="show">
      <CollectionAddProject @addProject="addProject" :key="renderAdd" />
    </div>
  <div v-if="showEditModal">
    <CollectionEditProject  @editProject="editProject" :updateData="updateData" :key="renderEdit" />
  </div>
  </div>
</template>

<script setup lang="ts">
import {ref} from "vue"

const show = ref(false)
const renderAdd = ref(0)
const renderEdit = ref(0)
const showEditModal = ref(false)
const updateData = ref({})

const projectsData = useAuthLazyFetch("https://v1-orm-gharpe.mercury.infinity-api.net/api/projects/",)
console.log("projectData----->",projectsData)

const showAdd = (data: Boolean) =>{
    show.value = data
    renderAdd.value++
    console.log("data in showAdd--->",data)
}

const showEdit= (data)=>{
  showEditModal.value = data 
  console.log("showEdit----?",data)
  renderEdit.value++
  updateData.value = data 
}

const addProject = (data:Object) => {
   const postOptions  ={
    body : {
    name: data.name,
    listing_type_name: data.listingTypeName,
    category: "Residential",
    sub_category: "Apartment",
    status:  "Fully Constructed",
    details: data.details,
    specifications: data.specifications,
    possession_date: "2023-04-07",
    age_of_the_project: data.ageOfProject,
    logo_url: data.logoUrl,
    total_project_area: 0,
    metric:"sq.ft",
    default_image_url: data.defaultImageUrl,
    visit_count: 0,
    rera_approved:  true,
    approve_status: "Active"
  },
    };
    console.log("body--->",postOptions)
    console.log("datain addprojectvsddj--->",data)
    const addData = useAuthLazyFetchPost("https://v1-orm-gharpe.mercury.infinity-api.net/api/projects/",postOptions)
    console.log("addDatatatattata---->",addData)
       }

const editProject = (data:Object) =>{
     const putOptions  ={
    body : {
    name: data.name,
    listing_type_name: data.listingTypeName,
    category: "Residential",
    sub_category: "Apartment",
    status:  "Fully Constructed",
    details: data.details,
    specifications: data.specifications,
    possession_date: "2023-04-07",
    age_of_the_project: data.ageOfProject,
    logo_url: data.logoUrl,
    total_project_area: 0,
    metric:"sq.ft",
    default_image_url: data.defaultImageUrl,
    visit_count: 0,
    rera_approved:  true,
    approve_status: "Active"
  },
    };
    console.log("datain asdsad--->",data)
    const editData = useAuthLazyFetchPut(`https://v1-orm-gharpe.mercury.infinity-api.net/api/projects/${data.uid}`,putOptions)
    console.log("addDatatatattata---->",editData)
}
const deleteProject = (data:object) => {
  console.log("data in deletePRoject---->",data)
const deleteOptions = {
    method: "DELETE",
  headers: {
    "Content-Type": "application/json",
    Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiZTk3YTIxZjM4ZDc4NDgwYjlhYjdhOTI0M2Q0NjViNzgiLCJkIjoiMTY4MDA5NyIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyODc4Mjd9.qFyxIJYJLihyxfui4QRMOLjJgwBr95z3N3lWRDz89ZU`,
  },
}
const deleteProjectData = useAuthLazyFetchDelete(`https://v1-orm-gharpe.mercury.infinity-api.net/api/projects/${data.uid}`,
deleteOptions
)
console.log("deleteProjectData--->",deleteProjectData)
    }
</script>
