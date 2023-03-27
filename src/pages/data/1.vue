<script lang="ts" setup>
const form1Storage = useStorage('form1', [] as any[])
const form1Data = computed(() => {
  return form1Storage.value.map((item: any) => {
    return {
      ...item,
      createdTime: item.createdTime,
    }
  })
})

const deleteAll = () => {
  ElMessageBox.confirm('This will permanently delete all data in form 1. Continue?', 'Warning', {
    confirmButtonText: 'OK',
    cancelButtonText: 'Cancel',
    type: 'warning',
  }).then(() => {
    form1Storage.value = []
    ElMessage({
      type: 'success',
      message: 'Delete all successfully!',
    })
  }).catch(() => {
    ElMessage({
      type: 'info',
      message: 'Delete canceled',
    })
  })
}
</script>

<template>
  <h1 text-3xl my-12 text-center font-bold>
    Form 1 Data
  </h1>
  <div class="toolbar" mx-4>
    <el-row class="mb-4" justify="end">
      <el-button type="danger" @click="deleteAll">
        Delete All
      </el-button>
    </el-row>
  </div>
  <div class="table" mx-4>
    <el-table :data="form1Data" :default-sort="{ prop: 'createdTime', order: 'descending' }" style="width: 100%">
      <el-table-column prop="id" label="ID" width="320" />
      <el-table-column prop="createdTime" label="Created Time" width="120" />
      <el-table-column prop="name" label="Name" width="120" />
      <el-table-column prop="region" label="Region" width="120" />
      <el-table-column prop="date1" label="Date 1" width="240" />
      <el-table-column prop="date2" label="Date 2" width="240" />
      <el-table-column prop="delivery" label="Delivery" width="100" />
      <el-table-column prop="type" label="Type" width="300" />
      <el-table-column prop="resource" label="Resource" width="160" />
      <el-table-column prop="desc" label="Description" width="160" />
    </el-table>
  </div>
</template>
