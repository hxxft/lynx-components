<template>
  <view ref="group">
    <slot></slot>
  </view>
</template>

<script>
  export default {
    props: {
      bindChange: Function
    },
    data() {
      return {
        values: []
      }
    },
    mounted() {
      this.up()
    },
    updated() {
      this.up()
    },
    methods: {
      xchange(curItem) {
        this.$children.forEach(item => {
          if (curItem !== item) {
            item.notify()
          } else {
            this.$emit('input',item.name)
          }
        })
        this.bindChange(curItem)
      },
      up() {
        var values = []
        this.$children.forEach(item => {
          item.callback = this.xchange
        })
      }
    }
  }
</script>