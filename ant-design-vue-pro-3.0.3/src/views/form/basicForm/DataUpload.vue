<template>
  <!-- hidden PageHeaderWrapper title demo -->
  <page-header-wrapper :title="false">
    <a-card :body-style="{ padding: '24px 32px' }" :bordered="false">
      <a-form @submit="handleSubmit" :form="form">
        <a-form-item
          :label="$t('form.basic-form.title.modelselect')"
          :labelCol="{ lg: { span: 7 }, sm: { span: 7 } }"
          :wrapperCol="{ lg: { span: 10 }, sm: { span: 17 } }"
        >
          <a-select v-model="queryParam.status" placeholder="请选择" default-value="0">
            <a-select-option value="0">电力负荷预测模型-v1</a-select-option>
          </a-select>
        </a-form-item>
        <!-- 添加目标公开单选框组 -->
        <a-form-item
          :label="$t('form.basic-form.title.parameter')"
          :labelCol="{ lg: { span: 7 }, sm: { span: 7 } }"
          :wrapperCol="{ lg: { span: 10 }, sm: { span: 17 } }"
        >
          <a-radio-group v-model="queryParam.publicTarget" v-decorator="['target', { initialValue: 1 }]">
            <a-radio :value="1">{{ $t('form.basic-form.parameter.freeze') }}</a-radio>
            <a-radio :value="2">{{ $t('form.basic-form.parameter.notfreeze') }}</a-radio>
          </a-radio-group>
        </a-form-item>
        <!-- 根据 showUploadComponent 控制上传组件的显示 -->
        <a-form-item
          v-if="showUploadComponent"
          :label="$t('form.basic-form.title.fileUpload')"
          :labelCol="{ lg: { span: 7 }, sm: { span: 7 } }"
          :wrapperCol="{ lg: { span: 10 }, sm: { span: 17 } }"
        >
          <a-upload
            name="file"
            :action="uploadAction"
            :before-upload="beforeUpload"
            :file-list="fileList"
            :showUploadList="true"
          >
            <a-button type="primary">
              <a-icon type="upload" />
              {{ $t('form.basic-form.form.uploadFile') }}
            </a-button>
          </a-upload>
        </a-form-item>
        <a-form-item :wrapperCol="{ span: 24 }" style="text-align: center">
          <a-button htmlType="submit" type="primary" @click="showUploadComponent = true">{{ $t('form.basic-form.form.datasubmit') }}</a-button>
          <a-button style="margin-left: 8px" @click="handlePredict">{{ $t('form.basic-form.form.predict') }}</a-button>
        </a-form-item>
      </a-form>
    </a-card>
  </page-header-wrapper>
</template>

<script>
import { Form, message, Upload, Icon } from 'ant-design-vue'

export default {
  name: 'BaseForm',
  components: {
    'a-upload': Upload,
    'a-icon': Icon
  },
  data () {
    return {
      form: Form.createForm(this),
      queryParam: {
        status: '0',
        publicTarget: 1
      },
      fileList: [], // 存储已选择的文件列表
      uploadAction: '/your-upload-url', // 实际的上传接口地址，需要根据后端接口修改
      showUploadComponent: false // 控制上传组件是否显示的标志
    }
  },
  methods: {
    // handleSubmit (e) {
    //   e.preventDefault()
    //   // 这里可以添加提交表单数据的逻辑，例如发送到后端
    //   // 目前只是简单地打印表单数据
    //   this.form.validateFields((err, values) => {
    //     if (!err) {
    //       console.log('Received values of form: ', values)
    //       message.success('上传成功')
    //     }
    //   })
    // },
    handlePredict () {
      message.success('预测成功')
    },
    beforeUpload (file) {
      // 在上传文件前的处理逻辑，例如文件格式检查等
      // 如果返回 false，则阻止文件上传
      this.fileList = [...this.fileList, file]
      return false
    }
  }
}
</script>

<style scoped>
</style>
