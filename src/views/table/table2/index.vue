<template>
  <div class="app-container">
    <el-table
      v-loading="listLoading"
      :data="list"
      element-loading-text="Loading"
      border
      fit
      highlight-current-row
    >
      <el-table-column align="center" label="序号" width="95">
        <template v-slot:default='slotProps'>
          {{ slotProps.$index }}
        </template>
      </el-table-column>
      <el-table-column label="ID" width='95' align='center'>
        <template v-slot:default='slotProps'>
          {{ slotProps.row.id }}
        </template>
      </el-table-column>
      <el-table-column label="Name" width="110" align="center">
        <template v-slot:default='slotProps'>
          {{ slotProps.row.name }}
        </template>
      </el-table-column>
      <el-table-column label="Password" width="110" align="center">
        <template v-slot:default='slotProps'>
          {{ slotProps.row.password }}
        </template>
      </el-table-column>
      <el-table-column label="测试列" width="110" align="center">
        <template v-slot:default='slotProps'>
          {{ slotProps.row}}
        </template>
      </el-table-column>
      <!-- <el-table-column class-name="status-col" label="Status" width="110" align="center">
        <template slot-scope="scope">
          <el-tag :type="scope.row.status | statusFilter">{{ scope.row.status }}</el-tag>
        </template>
      </el-table-column>
      <el-table-column align="center" prop="created_at" label="Display_time" width="200">
        <template slot-scope="scope">
          <i class="el-icon-time" />
          <span>{{ scope.row.display_time }}</span>
        </template>
      </el-table-column>
      <el-table-column align="center" prop="created_at" label="Display_time" width="200">
        <template slot-scope="scope">
          <i class="el-icon-time" />
          <span>{{ scope.row.display_time }}</span>
        </template>
      </el-table-column> -->
    </el-table>
  </div>
</template>

<script>
//import { getList } from '@/api/table'

export default {
  // filters: {
  //   statusFilter(status) {
  //     const statusMap = {
  //       published: 'success',
  //       draft: 'gray',
  //       deleted: 'danger'
  //     }
  //     return statusMap[status]
  //   }
  // },
  data() {
    return {
      list: null,
      listLoading: true
    }
  },
  created() {
    this.fetchData()
  },
  methods: {
    fetchData() {
      this.listLoading = true
      this.$axios.get('/api/user/getJson').then(response => {
        this.list = response.data
        this.listLoading = false
        
      })
    }
  }
}
</script>
