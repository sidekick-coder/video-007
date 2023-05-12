<script setup>
import DataTable from  './components/DataTable.vue'

const columns = [
  { label: 'Name', field: 'name' },
  { label: 'Age', field: 'age' },
  { label: 'Job', field: 'job' },
]

const rows = []

for (let i = 0; i < 10; i++) {
  rows.push({
    name: 'item-' + i,
    age: 'age-' + i,
    job: 'job-' + i,
  })
  
}

</script>
<template>
  <div class="h-screen w-screen flex items-center justify-center bg-gray-900" >
    <div class=" bg-white p-5 w-[500px] min-h-[300px] rounded">
      <div class="text-xl mb-4">
        Data table
      </div>

      <data-table :columns="columns" :rows="rows">

        <template #row-name="{ row, attrs }">
          <td class="text-purple-500" v-bind="attrs" >
            {{ row['name'] }}
          </td>
        </template>

      </data-table>

    </div>
  </div>
</template>