<template>
  <el-form ref="formDynamic" :model="formDynamic" label-width="60px">
    <el-form-item
      v-for="(item, index) in formDynamic.items"
      v-if="item.status"
      :key="index"
      :label="'主机 ' + item.index"
      :prop="'items.' + index + '.value'"
    >
      <el-row type="flex" justify="space-between">
        <el-col :span="8">
          <el-select v-model="formItem.selectOne">
            <el-option value="主机一">主机一</el-option>
            <el-option value="主机二">主机二</el-option>
            <el-option value="主机三">主机三</el-option>
          </el-select>
        </el-col>
        <el-col :span="8">
          <el-select v-model="formItem.selectTwo">
            <el-option value="主机一">主机一</el-option>
            <el-option value="主机二">主机二</el-option>
            <el-option value="主机三">主机三</el-option>
          </el-select>
        </el-col>
        <el-col :span="3">
          <el-button>添加</el-button>
        </el-col>
        <el-col :span="3">
          <el-button @click="handleRemove(index)">删除</el-button>
        </el-col>
      </el-row>
    </el-form-item>
    <el-form-item>
      <el-row type="flex" justify="end">
        <el-col :span="5">
          <el-button icon="el-icon-plus" @click="handleAdd">创建主机</el-button>
        </el-col>
      </el-row>
    </el-form-item>
  </el-form>
</template>
<script>
export default {
  data() {
    return {
      index: 1,
      formItem: {
        selectOne: '',
        selectTwo: ''
      },
      formDynamic: {
        items: [
          {
            value: '',
            index: 1,
            status: 1
          }
        ]
      }
    }
  },
  methods: {
    handleAdd() {
      this.index++
      this.formDynamic.items.push({
        value: '',
        index: this.index,
        status: 1
      })
    },
    handleRemove(index) {
      this.formDynamic.items[index].status = 0
    }
  }
}
</script>
