<template>
  <!-- input-select -->
  <div>
    <el-input
      v-if="item.type === 'selectInput'"
      :value="value? value.input : ''"
      @input="$emit('input', {input: $event, selectValue: value.selectValue})"
    >
      <el-select
        slot="prepend"
        :value="value? value.selectValue : ''"
        @input="$emit('input', {input: value.input , selectValue: $event })"
      >
        <el-option v-for="(val, key) in item.options" :key="key" :label="val" :value="key"></el-option>
      </el-select>
    </el-input>
  </div>
</template>

<script>
export default {
  props: {
    item: {
      type: Object,
      required: true
    },
    value: {
      type: [Object, String],
      required: false
    }
  }
}
</script>
