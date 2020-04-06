<template>
  <div>
    <el-form-item :label="item.label" :class="item.type === 'button' ? 'button-item': ''" :label-width="item.type === 'button' ? '0': '80px'">
      <!-- input-select -->
      <selectInput
        v-if="item.type === 'selectInput'"
        v-bind="$attrs"
        :item="item"
        v-on="$listeners"
      />
      <!-- inpt -->
      <el-input v-if="item.type === 'input'" :type="item.type" v-bind="$attrs" v-on="$listeners" />
      <!-- select -->
      <el-select v-if="item.type === 'select'" v-bind="$attrs" v-on="$listeners">
        <el-option v-for="(val, key) in item.options" :key="key" :label="val" :value="key"></el-option>
      </el-select>
      <!-- date-picker -->
      <el-date-picker
        v-if="item.type === 'datePicker'"
        :type="item.subtype"
        :format="item.format"
        v-bind="$attrs"
        range-separator="至"
        start-placeholder="开始时间"
        end-placeholder="结束时间"
        v-on="$listeners"
      ></el-date-picker>

      <el-button v-if="item.type === 'button'"  :type="item.subtype"  v-bind="$attrs" v-on="$listeners">{{ item.btnLabel }}</el-button>
      <!-- <span v-else>未知控件类型</span> -->
    </el-form-item>
  </div>
</template>

<script>
import selectInput from '../selectInput'

export default {
  components: {
    selectInput
  },
  props: {
    item: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      ajaxOptions: [
        {
          value: '0',
          label: '动态获取'
        }
      ]
    }
  },
  methods: {
    query1(e) {
      console.log(e)
    },
    onClick(e) {
      console.log(e)
    }
  }
}
</script>
