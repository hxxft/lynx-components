<template>
  <view ref="group">
    <slot></slot>
  </view>
</template>

<script>
  export default {
    props: {
      bindChange: {
        type: Function,
        default: function() {}
      },
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
        this.$emit('input',this.getCheckedName())
        this.bindChange(curItem)
      },
      getCheckedName() {
      	var newArray = [];
      	this.$children.forEach(item => {
      		if(item.status) {
      			newArray.push(item.name)
      		}
      	})
      	return newArray
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