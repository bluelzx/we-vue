<template>
  <div>
    <div class="weui-mask_transparent actionsheet__mask actionsheet__mask_show"
         v-show="currentValue && type === 'ios'" @click="currentValue = false"></div>
    <div class="weui-actionsheet weui-actionsheet_toggle" v-if="type === 'ios'" v-show="currentValue">
      <div class="weui-actionsheet__title" v-if="title">
        <p class="weui-actionsheet__title-text" v-html="title"></p>
      </div>
      <div class="weui-actionsheet__menu">
        <div class="weui-actionsheet__cell" v-for="item in actions" @click="itemClick(item)" v-text="item.name"></div>
      </div>
      <div class="weui-actionsheet__action" v-if="cancelText">
        <div class="weui-actionsheet__cell" @click="currentValue = false" v-html="cancelText"></div>
      </div>
    </div>

    <div class="weui-skin_android" v-if="type === 'android'" v-show="currentValue">
      <div class="weui-mask" @click="currentValue = false"></div>
      <div class="weui-actionsheet">
        <div class="weui-actionsheet__menu">
          <div v-for="item in actions" class="weui-actionsheet__cell" @click="itemClick(item)" v-text="item.name"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'wv-actionsheet',

    props: {
      type: {
        type: String,
        default: 'ios'
      },
      title: String,
      actions: {
        type: Array,
        default: []
      },
      cancelText: {
        type: String,
        default: 'Cancel'
      },
      value: Boolean
    },

    data () {
      return {
        currentValue: this.value
      }
    },

    watch: {
      currentValue (val) {
        this.$emit('input', val)
      },

      value (val) {
        this.currentValue = val
      }
    },

    methods: {
      itemClick (item) {
        if (item.method && typeof item.method === 'function') {
          item.method()
        }
        this.currentValue = false
      }
    },

    mounted () {
      if (this.value) {
        this.currentValue = true
      }
    }
  }
</script>

<style scoped lang="scss">
  .actionsheet__mask_show {
    display: block;
    transform-origin: 0px 0px 0px;
    opacity: 1;
    transform: scale(1, 1);
    background-color: rgba(0, 0, 0, 0.6);
  }
</style>
