<template>
  <view :style="{ backgroundColor: background }" class="container" @click="btnHandle">
    <label :style="{ color: foreground, fontSize: fontSize, fontWeight: fontWeight }">{{ text }}</label>
  </view>
</template>
<style>
  .container {
    justify-content: center;
    align-items: center;
    padding-left: 20;
    padding-right: 20;
    background-color: #FF5777;
    height: 200
  }

  .disabled_container {
    justify-content: center;
    align-items: center;
    padding-left: 20;
    padding-right: 20;
    height: 100;
    background-color: #d2d2d2;
  }
  .disabled {
    background-color: #d2d2d2;
  }
</style>
<script>
export default {
  props: {
    background: {
      type: String,
      default: '#ff5777'
    },
    foreground: {
      type: String,
      default: '#fff'
    },
    text: {
      type: String,
      default: ''
    },
    fontSize: {
      type: Number,
      default: 26
    },
    fontWeight: {
      type: String,
      default: 'normal'
    },
    disabled: {
      type: Boolean,
      default: false
    },
    onclick: {
      type: Function,
      default: function() {}
    }
  },
  methods: {
    btnHandle(e) {
      if(!this.disabled) {
        this.onclick(e)
        this.$emit('click')
      }
    }
  }
}
</script>