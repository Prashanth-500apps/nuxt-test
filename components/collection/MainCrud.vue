<template>
  <div>
    <div>
      <CollectionListCrud
        @openSlideout=";(open = true), renderAdd++"
        :formData="updateData"
        @editSlideout="showEdit"
        @deleteItem="deleteItem"
      />
    </div>
    <div v-if="open">
      <CollectionAddCrud @addedData="addedData" :key="renderAdd" />
    </div>
    <div v-if="showEditSlideout">
      <CollectionEditCrud
        @editData="editData"
        :updateValue="updateValue"
        :key="renderEdit"
      />
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

let open = ref(false)
let showEditSlideout = ref(false)
let renderAdd = ref(0)
let renderEdit = ref(0)

let formData = ref([
  {
    srNo: '1',
    name: 'Venkat',
    age: '22',
    gender: 'Male',
    dob: '2-5-1999',
    education: 'BTech',
  },
  {
    srNo: '2',
    name: 'Murali',
    age: '23',
    gender: 'Male',
    dob: '4-23-1998',
    education: 'BTech',
  },
  {
    srNo: '3',
    name: 'David',
    age: '25',
    gender: 'Male',
    dob: '3-4-1996',
    education: 'Inter2',
  },
])
let updateData = ref(formData.value)
let updateValue = ref([])

const showEdit = (data) => {
  showEditSlideout.value = true
  updateValue.value = data
  renderEdit.value++
}

onMounted(() => {
  updateData.value = JSON.parse(localStorage.getItem('updateData'))
})

const addedData = (data) => {
  updateData.value.push(data)
  localStorage.setItem('updateData', JSON.stringify(updateData.value))
  updateData.value = JSON.parse(localStorage.getItem('updateData'))
}

const editData = (data) => {
  updateData.value.find((item) => {
    if (item.srNo == data.srNo) {
      item.name = data.name
      item.age = data.age
      item.gender = data.gender
      item.dob = data.dob
      item.education = data.education
    }
  })
  localStorage.setItem('updateData', JSON.stringify(updateData.value))
}

const deleteItem = (data, index) => {
    console.log("data and index in delete---->",data,index)
  updateData.value.splice(index, 1)
  localStorage.setItem('updateData', JSON.stringify(updateData.value))
}
</script>
