# Element Plus Table Dragable

> 通过 `Element-Plus + Sortablejs`封装的表格拖拽

## 参数传递

| 参数名       | 参数解释        | 参数默认值   | 参数可选项           |
| ------------ | --------------- | ------------ | -------------------- |
| `pidKey`   | 树型关联的pid值 | `parentId` | 树型结构中的父级字段 |
| `limitPid` | 是否同级可拖拽  | `true`     | `true`/`false`   |

## 示例Demo
- demo.vue
```vue
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
```