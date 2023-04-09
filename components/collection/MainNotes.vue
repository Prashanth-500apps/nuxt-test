<template>
  <div>
    <div>
      <CollectionListNotes
        :noteInfo="noteInfo"
        @showAdd="showAdd"
        @edit="showEdit"
        @deleteProject="deleteProject"
      />
    </div>
    <div v-if="open">
      <CollectionAddNotes @addNote="addBody" :key="addRender" />
    </div>
    <div v-if="showEditModal">
      <CollectionEditNotes
        @editNote="editProject"
        :updateNote="updateNote"
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
const showEditModal = ref(false)
const updateNote = ref({})
const noteInfo = ref([])
let projectId = ref('')

const { data: notesData } = useAuthLazyFetch(
  `https://v1-orm-lib.mars.hipso.cc/api/notes/CONTACTS/string?project_id=12&offset=0&limit=100&sort_column=id&sort_direction=desc`,
)
noteInfo.value = notesData.value
const showAdd = (data) => {
  open.value = data
  addRender.value++
}
const showEdit = (data) => {
  showEditModal.value = true
  editRender.value++
  updateNote.value = data
}
const addBody = async (body: Object) => {
  const postOptions = {
    body: body,
  }
  await useAuthLazyFetchPost(
    'https://v1-orm-lib.mars.hipso.cc/api/notes/CONTACTS/string',
    postOptions,
  )
  noteInfo.value.unshift(body)
}

const editProject = async (body: object) => {
  const putOptions = {
    body: body,
  }
  await useAuthLazyFetchPut(
    `https://v1-orm-lib.mars.hipso.cc/api/notes/${body.uid}`,
    putOptions,
  )
  const { data: response } = await useAuthLazyFetch(
    'https://v1-orm-lib.mars.hipso.cc/api/notes/CONTACTS/string?project_id=12&offset=0&limit=100&sort_column=id&sort_direction=desc',
  )
  noteInfo.value = response.value
}

const deleteProject = async (data: object, index) => {
  await useAuthLazyFetchDelete(
    `https://v1-orm-lib.mars.hipso.cc/api/notes/${data.uid}`,
  )
  noteInfo.value.splice(index, 1)
}
</script>
