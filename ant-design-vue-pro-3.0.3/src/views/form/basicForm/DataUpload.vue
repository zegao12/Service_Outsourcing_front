<template>
  <!-- hidden PageHeaderWrapper title demo -->
  <page-header-wrapper :title="false" >
    <a-card :body-style="{padding: '24px 32px'}" :bordered="false">
      <a-form @submit="handleSubmit" :form="form">
        <a-form-item
          :label="$t('form.basic-form.title.modelselect')"
          :labelCol="{lg: {span: 7}, sm: {span: 7}}"
          :wrapperCol="{lg: {span: 10}, sm: {span: 17} }">
          <a-select v-model="queryParam.status" placeholder="请选择" default-value="0">
            <a-select-option value="0">广告位招租</a-select-option>
            <a-select-option value="1">广告位招租</a-select-option>
            <a-select-option value="2">广告位招租</a-select-option>
          </a-select>
        </a-form-item>
        <a-form-item
          :wrapperCol="{ span: 24 }"
          style="text-align: center"
        >
          <a-button htmlType="submit" type="primary">{{ $t('form.basic-form.form.datasubmit') }}</a-button>
          <a-button style="margin-left: 8px" @click="handlePredict">{{ $t('form.basic-form.form.predict') }}</a-button>
        </a-form-item>
      </a-form>
    </a-card>
  </page-header-wrapper>
</template>

<script>
import { Form, message } from 'ant-design-vue' // 确保引入了 Form 组件

export default {
  name: 'BaseForm',
  data () {
    return {
      form: Form.createForm(this), // 初始化表单
      queryParam: {
        status: '0'
      }
    }
  },
  methods: {
    // handler
    handleSubmit (e) {
      e.preventDefault()
      this.form.validateFields((err, values) => {
        if (!err) {
          console.log('Received values of form: ', values)
          // 这里可以添加发送数据到后端的逻辑
          // 假设数据发送成功（实际应用中需要根据后端返回状态判断）
          message.success('上传成功')
        }
      })
    },
    handlePredict () {
      // 这里可以添加实际的预测逻辑，比如调用后端接口进行预测
      // 假设预测成功（实际应用中需要根据实际情况判断）
      message.success('预测成功')
    }
  }
}
</script>
