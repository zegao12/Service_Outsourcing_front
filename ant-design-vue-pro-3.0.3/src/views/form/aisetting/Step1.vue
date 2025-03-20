<template>
  <div>
    <a-form :form="form" style="max-width: 500px; margin: 40px auto 0;">
      <a-form-item
        label="模型版本"
        :labelCol="labelCol"
        :wrapperCol="wrapperCol"
      >
        <a-select
          placeholder="2302beta01"
          v-decorator="['paymentUser', { rules: [{required: true, message: '模型版本必须填写'}] }]">
          <a-select-option value="1">2302beta01</a-select-option>
        </a-select>
      </a-form-item>
      <a-form-item
        label="模型类型"
        :labelCol="labelCol"
        :wrapperCol="wrapperCol"
      >
        <a-input-group
          style="display: inline-block; vertical-align: middle"
          :compact="true"
        >
          <a-select defaultValue="alipay" style="width: 100px">
            <a-select-option value="alipay">PyTorch</a-select-option>
          </a-select>
          <a-input
            :style="{width: 'calc(100% - 100px)'}"
            v-decorator="['payType', { initialValue: '太赫兹图像16类危险物品', rules: [{required: true, message: '模型类型必须填写'}]}]"
          />
        </a-input-group>
      </a-form-item>
      <a-form-item
        label="操作员姓名"
        :labelCol="labelCol"
        :wrapperCol="wrapperCol"
      >
        <a-input v-decorator="['name', { initialValue: 'Alex', rules: [{required: true, message: '操作员姓名必须核对'}] }]"/>
      </a-form-item>
      <a-form-item
        label="操作备注"
        :labelCol="labelCol"
        :wrapperCol="wrapperCol"
      >
        <a-input v-decorator="['momey', { initialValue: '230222手动升级', rules: [{required: true, message: '操作备注必须填写'}] }]"/>
      </a-form-item>
      <a-form-item :wrapperCol="{span: 19, offset: 5}">
        <a-button type="primary" @click="nextStep">下一步</a-button>
      </a-form-item>
    </a-form>
    <a-divider />
    <div class="step-form-style-desc">
      <h3>说明</h3>
      <p>对AI模型进行升级并部署</p>
      <p>确认部署后，新模型将下载并加载至显存，无法退回旧版本模型。</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Step1',
  data () {
    return {
      labelCol: { lg: { span: 5 }, sm: { span: 5 } },
      wrapperCol: { lg: { span: 19 }, sm: { span: 19 } },
      form: this.$form.createForm(this)
    }
  },
  methods: {
    nextStep () {
      const { form: { validateFields } } = this
      // 先校验，通过表单校验后，才进入下一步
      validateFields((err, values) => {
        if (!err) {
          this.$emit('nextStep')
        }
      })
    }
  }
}
</script>

<style lang="less" scoped>
.step-form-style-desc {
  padding: 0 56px;
  color: rgba(0,0,0,.45);

  h3 {
    margin: 0 0 12px;
    color: rgba(0,0,0,.45);
    font-size: 16px;
    line-height: 32px;
  }

  h4 {
    margin: 0 0 4px;
    color: rgba(0,0,0,.45);
    font-size: 14px;
    line-height: 22px;
  }

  p {
    margin-top: 0;
    margin-bottom: 12px;
    line-height: 22px;
  }
}
</style>
