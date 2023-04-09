<template>
  <div>
    <div>
      <CollectionListProjects
        :projectInfo="projectInfo"
        @showAdd="showAdd"
        @showEdit="showEdit"
        @deleteProject="deleteProject"
      />
    </div>
    <div v-if="show">
      <CollectionAddProjects @addProject="addProject" :key="renderAdd" />
    </div>
    <div v-if="showEditModal">
      <CollectionEditProjects
        @editProject="editProject"
        :updateData="updateData"
        :key="renderEdit"
      />
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

const show = ref(false)
const renderAdd = ref(0)
const renderEdit = ref(0)
const showEditModal = ref(false)
const updateData = ref({})
const url = ref('https://v1-orm-gharpe.mercury.infinity-api.net/api/projects/')

const projectsData = useAuthLazyFetch(url.value)

const showAdd = (data: any) => {
  show.value = data
  renderAdd.value++
}

const showEdit = (data) => {
  showEditModal.value = data
  renderEdit.value++
  updateData.value = data
}

let projectInfo = ref(projectsData.data._rawValue)

const addProject = async (body: Object) => {
  const postOptions = {
    body: body,
  }
  await useAuthLazyFetchPost(url.value, postOptions)
  projectInfo.value.unshift(body)
}

const editProject = async (body: Object) => {
  const putOptions = {
    body: body,
  }
  await useAuthLazyFetchPut(`${url.value}${body.uid}`, putOptions)
  const { data: response } = await useAuthLazyFetch(url.value)
  projectInfo.value = response.value
}

const deleteProject = async (data: object, index) => {
  await useAuthLazyFetchDelete(`${url.value}${data.uid}`)
  projectInfo.value.splice(index, 1)
}
</script>
