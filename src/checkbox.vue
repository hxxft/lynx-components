<template>
  <view @click="change" ref="checkbox">
   <img :src="pic" :style="{width: width, height: height}"></img>
  </view>
</template>

<script>

export default {
  props: {
   picArray: Array,
    name: {
      type: String,
      default: ''
    },
    height:{
      type: Number,
      default: 48
    },
    width:{
      type: Number,
      default: 48
    },
    checked: {
      type: Boolean,
      default: false
    },
    disabled: {
      type: Boolean,
      default: false
    }
  },
  created() {
    if(this.disabled) {
      this.pic = this.picArray[2]
    } else if(this.checked) {
      this.pic = this.picArray[1]
    } else {
      this.pic = this.picArray[0]
    }
  },
  data() {
    return {
      pic: '',
      status: this.checked
    }
  },
   methods: {
    change() {
      if(!this.disabled) {
        if(this.pic == this.picArray[1]) {
          this.pic = this.picArray[0]
          this.status = false
        }else {
          this.pic = this.picArray[1]
          this.status = true
        }
        this.callback(this)
      }
    }
  }
}
</script>
