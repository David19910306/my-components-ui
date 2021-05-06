<template>
  <div class="my-radio" :class="{'active': label === value}">
    <span class="my-radio-input">
      <input type="radio" :name="name" :value="label" v-model="myModel" />
    </span>
    <span class="my-radio-text"><slot>{{label}}</slot></span>
  </div>
</template>

<script lang="ts">
import { computed, defineComponent } from 'vue'

export default defineComponent({
  name: 'MyRadio',
  props: {
    label: {
      type: [String, Number, Boolean],
      default: ''
    },
    name: {
      type: String,
      default: ''
    },
    value: null // 不进行任何类型校验
  },
  setup (props, { emit }) {
    const myModel = computed({
      get () {
        // console.log(props.value)
        return props.value
      },
      set (value) {
        emit('inputChange', value)
      }
    })

    return { myModel }
  }
})
</script>

<style lang="scss" scoped>
.my-radio-text{
  color: #606266;
  font-weight:400;
}
.active{
  .my-radio-text{
    color: #409eff;
    font-weight: 800;
    font-size: 18px;
  }

}
</style>
