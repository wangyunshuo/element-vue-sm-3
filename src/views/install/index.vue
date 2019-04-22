<template>
  <div>
    <el-dialog
      :visible.sync="modal1"
      :title="title"
      :close-on-click-modal="false"
      :close-on-press-escape="false"
    >
      <createDataCenter v-if="isShow==1"/>
      <createColony v-if="isShow==2"/>
      <addHost v-if="isShow==3"/>
      <div slot="footer">
        <el-button type="primary" size="small" @click="last(title)">上一步</el-button>
        <el-button size="small" @click="skip(title)">跳过</el-button>
        <el-button type="primary" size="small" @click="next(title)">下一步</el-button>
      </div>
    </el-dialog>
    <el-button type="primary" @click="create">创建</el-button>
  </div>
</template>
<script>
import { getList } from '@/api/table'
import createDataCenter from './step/createDataCenter.vue'
import createColony from './step/createColony.vue'
import addHost from './step/addHost.vue'
export default {
  components: {
    createDataCenter,
    createColony,
    addHost
  },
  data() {
    return {
      isShow: 1,
      modal1: false,
      title: '新建数据中心'
    }
  },
  methods: {
    // 下一步
    next(title) {
      switch (title) {
        case '新建数据中心':
          this.title = '新建集群'
          this.isShow = 2
          break
        case '新建集群':
          this.title = '添加主机'
          this.isShow = 3
          break
      }
    },
    // 上一步
    last(title) {
      switch (title) {
        case '新建数据中心':
          this.title = '新建数据中心'
          this.isShow = 1
          break
        case '新建集群':
          this.title = '新建数据中心'
          this.isShow = 1
          break
        case '添加主机':
          this.title = '新建集群'
          this.isShow = 2
          break
      }
    },
    // 跳过
    skip(title) {
      switch (title) {
        case '新建数据中心':
          this.title = '新建集群'
          this.isShow = 2
          break
        case '新建集群':
          this.title = '添加主机'
          this.isShow = 3
          break
      }
    },
    // 创建
    create() {
      getList()
      this.modal1 = true
      this.title = '新建数据中心'
      this.isShow = 1
    }
  }
}
</script>
<style rel="stylesheet/scss" lang="scss" scoped>
</style>
