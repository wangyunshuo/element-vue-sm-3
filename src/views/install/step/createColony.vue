<template>
  <el-form :model="formItem" label-width="100px">
    <el-form-item label="选择">
      <el-row>
        <el-col :span="18">
          <el-select v-model="formItem.select" placeholder="请选择">
            <el-option :value="1" :label="'集群一'">集群一</el-option>
            <el-option :value="2" :label="'集群二'">集群二</el-option>
            <el-option :value="3" :label="'集群三'">集群三</el-option>
          </el-select>
        </el-col>
      </el-row>
    </el-form-item>
    <el-form-item label="集群名称">
      <el-row>
        <el-col :span="18">
          <el-input v-model="formItem.input" placeholder="请填写数据中心名称"/>
        </el-col>
        <el-col :span="4" :offset="1">
          <el-button>添加</el-button>
        </el-col>
      </el-row>
    </el-form-item>
  </el-form>
</template>
<script>
export default {
  data() {
    return {
      modal1: true,
      formItem: {
        select: '',
        input: ''
      },
      option: [
        {
          lable: '集群一',
          value: '1'
        },
        {
          lable: '集群二',
          value: '2'
        },
        {
          lable: '集群三',
          value: '3'
        }
      ]
    }
  },
  methods: {
    ok() {
      this.$Message.info('Clicked ok')
    },
    cancel() {
      this.modal1 = false
      this.$Message.info('Clicked cancel')
    }
  }
}
</script>
<style rel="stylesheet/scss" lang="scss" scoped>
</style>
