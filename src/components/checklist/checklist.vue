<template>
  <div>
    <div v-if="title" class="weui-cells__title" v-html="title"></div>
    <div class="weui-cells weui-cells_checkbox">
      <label v-for="option in options" class="weui-cell weui-check__label"
             :class="{ 'weui-check__label-disabled': option.disabled }">
        <div class="weui-cell__hd">
          <input type="checkbox" class="weui-check" v-model="currentValue" :disabled="option.disabled"
                 :value="option.value || option">
          <i class="weui-icon-checked"></i>
        </div>
        <div class="weui-cell__bd">
          <p v-text="option.label || option"></p>
        </div>
      </label>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'wv-checklist',

    props: {
      max: Number,
      title: String,
      align: String,
      options: {
        type: Array,
        required: true
      },
      value: Array
    },

    data () {
      return {
        currentValue: this.value
      }
    },

    computed: {
      limit () {
        return this.max < this.currentValue.length
      }
    },

    watch: {
      currentValue (val) {
        if (this.limit) val.pop()
        this.$emit('input', val)
        this.$emit('change', val)
      },

      value (val) {
        this.currentValue = val
      }
    }
  }
</script>

<style scoped lang="scss">
  .weui-check__label-disabled {
    background-color: rgba(0, 0, 0, 0.1)
  }
</style>
