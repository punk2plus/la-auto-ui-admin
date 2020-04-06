<template>
  <el-form :model="value" v-bind="formConfig">
    <auto-create-form-item
      v-for="item in formConfig.formItemList"
      :key="item.key"
      :item="item"
      v-bind="item"
      :value="value[item.key]"
      @input="handleInput($event, item.key, item.type)"
      @click="onClick($event, item)"
    />
    <slot></slot>
  </el-form>
</template>



<script>
import autoCreateFormItem from './auto-create-form-item'

// @click="onClick($event, item)"
// @query="query"

export default {
  components: {
    autoCreateFormItem
  },
  props: {
    formConfig: {
      type: Object,
      required: true
    },
    value: {
      type: Object,
      required: true
    }
  },
  mounted() {
    this.setDefaultValue()
  },
  methods: {
    handleInput(val, key) {
      console.log('====>>>', val)
      // console.log('====>>>', key)
      // console.log('====>>>', type)
      console.log('===1111=>>>', { ...this.value, [key]: val })
      this.$emit('input', { ...this.value, [key]: val })
    },
    setDefaultValue() {
      const formData = { ...this.value }
      // 设置默认值
      this.formConfig.formItemList.forEach(item => {
        const { key, value } = item

        if (formData[key] === undefined || formData[key] === null) {
          console.log(key, formData[key])
          console.log(value)
          formData[key] = value
        }
      })
      this.$emit('input', { ...formData })
    },
    onClick(e, item) {
      if (item.type === 'button')
        this.$emit(item.clickMethodName, {e, click: item.onClick} )
 
    }
  }
}
</script>