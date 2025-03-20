<template>
  <div>
    <a-form>
      <a-result title="操作成功" :is-success="true" sub-title="预计2分钟内完成部署" style="max-width: 560px; margin: 40px auto 0;">
        <div class="information">
          <a-row>
            <a-col :sm="8" :xs="24">模型版本：</a-col>
            <a-col :sm="16" :xs="24">2302beta01</a-col>
          </a-row>
          <a-row>
            <a-col :sm="8" :xs="24">模型类型：</a-col>
            <a-col :sm="16" :xs="24">PyTorch-太赫兹图像16类危险物品</a-col>
          </a-row>
          <a-row>
            <a-col :sm="8" :xs="24">操作员姓名：</a-col>
            <a-col :sm="16" :xs="24">Alex</a-col>
          </a-row>
          <a-row>
            <a-col :sm="8" :xs="24">操作备注：</a-col>
            <a-col :sm="16" :xs="24">230222手动升级</a-col>
          </a-row>
          <a-row>
            <a-col :sm="8" :xs="24">过滤阈值</a-col>
            <a-col :sm="16" :xs="24"><span class="threshold">25</span> %</a-col>
          </a-row>
        </div>
        <template #extra>
          <a-button type="primary" @click="finish">刷新部署状态</a-button>
          <a-button style="margin-left: 8px" @click="toOrderList">开始安检</a-button>
        </template>
      </a-result>
    </a-form>
  </div>
</template>

<script>
export default {
  name: 'Step3',
  data () {
    return {
      loading: false
    }
  },
  methods: {
    finish () {
      this.$emit('finish')
    },
    toOrderList () {
      this.$router.push('/list/table-list')
    }
  }
}
</script>
<style lang="less" scoped>
  .information {
    line-height: 22px;

    .ant-row:not(:last-child) {
      margin-bottom: 24px;
    }
  }
  .money {
    font-family: "Helvetica Neue",sans-serif;
    font-weight: 500;
    font-size: 20px;
    line-height: 14px;
  }
</style>
