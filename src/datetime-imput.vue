<template>
<div class="flatpickr">
    <label>{{label}}</label>
    <input type="text" :placeholder="placeholder" data-input ref="datetimeInput">
    <a class="input-button" title="clear" data-clear>
        <i class="icon-close" @click.prevent="handleClear">x</i>
    </a>
</div>
</template>

<style>
  @import '../node_modules/flatpickr/dist/themes/airbnb.css';
  @import './assets/flatpickr-alayacare.css';

  label{
      display: block;
      margin: 10px 0;
  }
    input{
        width: 210px;
    }
</style>

<script type="text/babel">
  import Flatpickr from 'flatpickr';
  export default {
      props: {
          options: {
              type: Object,
              default() {},
          },
          label: String,
          placeholder: String,
          val: String,
          value: {},
      },
      data() {
          return {
              interVal: this.value,
              flatPickr: null,
          };
      },
      methods: {
          changeVal() {
              this.$emit('input', this.interVal);
          },
          handleClear() {
              this.flatPickr && this.flatPickr.clear();
          },
      },
      watch: {
          interVal(val) {
              this.interVal = val;
              this.$emit('input', this.interVal);
          },
      },
      mounted() {
          const pickrEl = this.$refs.datetimeInput;
          this.flatPickr = new Flatpickr(pickrEl, this.options);
      },
      beforeDestroy() {
          if (this.flatPickr) {
              this.flatPickr.destroy();
              this.flatPickr = null;
          }
      },
  }
</script>
