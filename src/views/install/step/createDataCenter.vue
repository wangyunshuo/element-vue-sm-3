<template>
  <el-form :model="formItem" label-width="130px">
    <el-form-item label="数据中心名称">
      <el-row>
        <el-col :span="18">
          <el-input v-model="formItem.input" placeholder="请填写数据中心名称"/>
        </el-col>
        <el-col :span="3" :offset="1">
          <el-button @click="add">添加</el-button>
        </el-col>
      </el-row>
    </el-form-item>
  </el-form>
</template>
<script>
export default {
  data() {
    return {
      formItem: {
        input: ''
      }
    }
  },
  methods: {
    // 添加
    add() {
      this.$message.success('添加成功')
    }
  }
}
</script>
<style rel="stylesheet/scss" lang="scss" scoped>
</style>
