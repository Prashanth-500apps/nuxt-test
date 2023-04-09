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
const url = ref(`https://v1-orm-gharpe.mercury.infinity-api.net/api/leads/`)

const usersData = useAuthLazyFetch(url.value)

const openLead = (data) => {
  open.value = data
  addRender.value++
}

const showEdit = (data) => {
  showEditSidebar.value = true
  editRender.value++
  updateLead.value = data
}

let userInfo = ref(usersData.data._rawValue)

const addBody = async (body: Object) => {
  const postOptions = {
    body: body,
  }
  await useAuthLazyFetchPost(url.value, postOptions)
  userInfo.value.unshift(body)
}

const editProject = async (body: Object) => {
  const putOptions = {
    body: body,
  }
  await useAuthLazyFetchPut(`${url.value}${body.uid}`, putOptions)
  const { data: response } = await useAuthLazyFetch(url.value)
  userInfo.value = response.value
}

const deleteProject = async (data: object, index) => {
  await useAuthLazyFetchDelete(
    `${url.value}${data.uid}`,
  )
  userInfo.value.splice(index, 1)
}
</script>
