<template>
  <div>
    <div>
      <CollectionBankList :bankInfo="bankInfo" @openAdd="showAdd" />
    </div>
    <div v-if="open">
      <CollectionBankAdd @addData="addBody" :key="addRender" />
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref,onMounted } from 'vue'

const open = ref(false)
const addRender = ref(0)
const bankInfo = ref([])

const { data: getData } = useAuthLazyFetch(
  `https://v7-stark-db-orm.mercury.infinity-api.net/api/question-bank/?offset=0&limit=100&sort_column=id&sort_direction=desc
`,
)
bankInfo.value = getData.value

const showAdd = (data) => {
  open.value = data
  addRender.value++
}

const addBody =  (body: object) => {
  const postOptions = {
    body: body,
  }
 const adddData =   useAuthLazyFetchPost(
    'https://v7-stark-db-orm.mercury.infinity-api.net/api/question-bank/bulk',
    postOptions,
  )
  bankInfo.value.unshift(body[0])
}
</script>
