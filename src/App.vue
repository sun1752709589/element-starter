<template>
  <div id="app">
    <img src="./assets/logo.png">
    <div>
      <el-button @click="startHacking">开始</el-button>
    </div>
    <div class="tableData">
      <el-table
        :data="tableData"
        style="width: 100%">
        <el-table-column
          prop="id"
          label="ID"
          width="90">
        </el-table-column>
        <el-table-column
          prop="ctime"
          label="日期"
          width="360">
        </el-table-column>
        <el-table-column
          prop="q"
          label="关键字"
          width="360">
        </el-table-column>
        <el-table-column
          prop="ip"
          label="IP地址"
          width="360">
        </el-table-column>
      </el-table>
    </div>
  </div>
</template>

<script>
const axios = require('axios');
export default {
  data() {
    return {
      tableData: [{}]
    }
  },
  methods: {
    startHacking () {
      var self = this;
      axios.get('https://book.51read.site/admin/search_histories.json')
        .then(function (response) {
          self.tableData = response.data.histories
        })
      this.$notify({
        title: '获取浏览历史成果！',
        type: 'success',
        message: 'We\'ve laid the ground work for you. It\'s time for you to build something epic!',
        duration: 1000
      })
    }
  }
}
</script>

<style>
#app {
  font-family: Helvetica, sans-serif;
  text-align: center;
}
.tableData {
  margin: 0 auto;
  position: absolute;
  left: 15%;
}
</style>
