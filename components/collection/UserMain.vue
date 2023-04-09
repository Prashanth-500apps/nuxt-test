<template>
  <div>
    <div>
      <CollectionUserList
        :userInfo="userInfo"
        @openLead="openLead"
        @edit="showEdit"
        @deleteProject="deleteProject"
      />
    </div>
    <div v-if="open">
      <CollectionUserAdd @addLeadBody="addBody" :key="addRender" />
    </div>
    <div v-if="showEditSidebar">
      <CollectionUserEdit
        @editLeadBody="editProject"
        :updateLead="updateLead"
        :key="editRender"
      />
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const open = ref(false)
const addRender = ref(0)
const editRender = ref(0)
const showEditSidebar = ref(false)
const updateLead = ref({})
// const url = ref('https://v1-orm-gharpe.mercury.infinity-api.net/api/projects/')

const usersData = useAuthLazyFetch(
  "https://v1-orm-gharpe.mercury.infinity-api.net/api/leads/",
)
console.log("userdData--->",usersData)

const openLead = (data) => {
    open.value = data
    addRender.value++
    console.log("data in openLead---->",data)
}

let editIndex = ref('')

const showEdit = (data) => {
  showEditSidebar.value = true
  console.log("data inedit--->",data, showEditSidebar.value)
  editRender.value++
  updateLead.value = data
}

let userInfo = ref(usersData.data._rawValue)

const addBody = (body: Object) => {
  const postOptions = {
    body: body,
  }
  console.log("body in add--->",)
  const addData = useAuthLazyFetchPost("https://v1-orm-gharpe.mercury.infinity-api.net/api/leads/",postOptions
  )
  userInfo.value.unshift(body)
}

const editProject = (body: Object) => {
  const putOptions = {
    body: body,
  }
  const editData = useAuthLazyFetchPut(
    `https://v1-orm-gharpe.mercury.infinity-api.net/api/leads/${body.uid}`,
    putOptions,
  )
//     const { data: response } =  useAuthLazyFetch("https://v1-orm-gharpe.mercury.infinity-api.net/api/leads/?offset=0&limit=100&sort_column=id&sort_direction=desc","");
// console.log("response in edit--->",response)
// userInfo.value = response.value;
 // updateLead.value.$set(editIndex.value,body)
}

const deleteProject = (data: object, index) => {
  const deleteProjectData = useAuthLazyFetchDelete(
    `https://v1-orm-gharpe.mercury.infinity-api.net/api/leads/${data.uid}`,
  )
  userInfo.value.splice(index, 1)
}
</script>
