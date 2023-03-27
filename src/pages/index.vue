<script setup lang="ts" generic="T extends any, O extends any">
defineOptions({
  name: 'IndexPage',
})
</script>

<template>
  <div text-center>
    <h1 my-12 font-bold text-3xl>
      Test Forms
    </h1>
    <a href="/form/1" btn mx-4>
      form 1
    </a>

    <a href="/data/1" btn mx-4>
      data 1
    </a>
  </div>
</template>
