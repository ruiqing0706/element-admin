<template>
  <div>
    <el-button icon="el-icon-back" round @click="$emit('option-changed')">返回</el-button>
    <el-collapse value="base-info" accordion>
      <el-collapse-item title="基本信息" name="base-info">
        <el-form :model="detail" :label-width="labelWidth">
          <input-item-view label="ID">{{ detail.id }}</input-item-view>
          <input-item-view label="上级ID">{{ detail.parentId }}</input-item-view>
          <input-item-view label="启用状态">{{ detail.state | translateState }}</input-item-view>
          <input-item-view label="字典类型">{{ getDictionaryTypeName(detail.type) }}</input-item-view>
          <input-item-view label="字典名称">{{ detail.name }}</input-item-view>
          <input-item-view label="字典规则码">{{ detail.code }}</input-item-view>
          <input-item-view label="字典编号">{{ detail.index }}</input-item-view>
          <text-item-view label="字典备注">{{ detail.remark }}</text-item-view>
        </el-form>
      </el-collapse-item>
      <el-collapse-item title="审计信息" name="audit-info">
        <audit-info :detail="detail" :label-width="labelWidth"/>
      </el-collapse-item>
    </el-collapse>
  </div>
</template>

<script>
import mixins from './mixins'

export default {
  mixins: [mixins],
  props: {
    detail: {
      required: true,
      type: Object,
      default: () => {}
    }
  },
  data() {
    return {
      labelWidth: '200px'
    }
  },
  activated() {
    this.queryAllDictionaryType()
  }
}
</script>

<style lang="scss" scoped>
  .el-button {
    margin-bottom: 10px;
  }
</style>
