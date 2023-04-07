<template>
  <div>
    <CollectionListUser :userData="userData"/>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const userData = useAuthLazyFetch("https://v1-orm-emc2-messaging.mars.hipso.cc/user-prefs/",)
console.log("userData---->",userData)
</script>
