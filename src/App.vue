<script setup lang="ts">
import { ref } from 'vue';
import DragTable from './components/drag-table.vue'
import mockData from './mock';
const tableData = ref<any[]>([])
const initialData = () => {
  tableData.value = mockData
}
const changeTableData = (datas: any[]) => {
  tableData.value = datas
}
initialData()
</script>

<template>
  <div class="container">
    <drag-table limit-pid @change-data="changeTableData">
      <el-table :data="tableData" :row-key="(row: any) => String(row.id)" :tree-props="{ children: 'children' }">
        <el-table-column label="层级名称" prop="name"></el-table-column>
      </el-table>
    </drag-table>
  </div>
</template>
