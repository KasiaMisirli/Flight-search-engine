<template>
  <button v-on:click="$emit('click')" class="spinner-btn">
    <div v-if="isSubmitting"></div>
    <div class="v-spinner" v-show="loading">
      <div class="v-clip" v-bind:style="spinnerStyle">
      </div>
    </div>
    <div v-if="!isSubmitting"></div>
  </button>
</template>

<script>
export default {
 data() {
  return {
    isLoading: false,
    status: '',
  }
 },
  name: 'ClipLoader',
  props: {
    loading: {
      type: Boolean,
      default: true
    },
    isSubmitting: {
      type: Boolean,
      status: false
    },
  	color: {
      type: String,
      default: '#FFFFFF'
    },
  	size: {
      type: String,
      default: '20px'
    },
    radius: {
      type: String,
      default: '100%'
    }
  },
  computed: {
    spinnerStyle () {
      return {
        height: this.size,
        width: this.size,
        borderWidth: '3px',
        borderStyle: 'solid',
        borderColor: this.color + ' ' + this.color + ' transparent',
        borderRadius: this.radius,
        background: 'transparent'
      }
    }
  }
}
</script>

<style>
.spinner-btn {
  background-color: lightgrey;
  height: 40px;
  width: 100px;
  border-radius: 5px;
}
.v-spinner
{
  text-align: center;
}
.v-spinner .v-clip
{
  -webkit-animation: v-clipDelay 0.75s 0s infinite linear;
          animation: v-clipDelay 0.75s 0s infinite linear;
  -webkit-animation-fill-mode: both;
          animation-fill-mode: both;
  display: inline-block;
}
@-webkit-keyframes v-clipDelay
{
  0%
  {
    -webkit-transform: rotate(0deg) scale(1);
            transform: rotate(0deg) scale(1);
  }
  50%
  {
    -webkit-transform: rotate(180deg) scale(0.8);
            transform: rotate(180deg) scale(0.8);
  }
  100%
  {
    -webkit-transform: rotate(360deg) scale(1);
            transform: rotate(360deg) scale(1);
  }
}
@keyframes v-clipDelay
{
  0%
  {
    -webkit-transform: rotate(0deg) scale(1);
            transform: rotate(0deg) scale(1);
  }
  50%
  {
    -webkit-transform: rotate(180deg) scale(0.8);
            transform: rotate(180deg) scale(0.8);
  }
  100%
  {
    -webkit-transform: rotate(360deg) scale(1);
            transform: rotate(360deg) scale(1);
  }
}
</style>

