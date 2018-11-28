<template>
  <div v-if="!isLoading" >
    <button class="spinner-btn" v-on:click="onSubmit">Submit</button>
  </div>
  <div v-else>
    <button v-on:click="onSubmit" class="spinner-btn button" v-bind:is-loading="isLoading" v-bind:disabled="isLoading" >
      <div class="v-spinner" v-show="isLoading">
        <div class="v-clip" v-bind:style="spinnerStyle">
        </div>
      </div>
    </button>
  </div>

</template>
<script>
export default {
  name: 'ClipLoader',
  data() {
      return {
          isLoading: false,
          status: '',
          data: {
          buttonname: "this is the name",
          }
      }
  },
  props: {
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
  },
  methods: {
      onSubmit() {
          this.isLoading = true
          setTimeout(() => {
            this.isLoading = false
          }, 2000)


      }
  }
}
</script>
<style>
  .button {
    height: 60px;
    width: 100px;
    background-color: blue;
  }
  .spinner-btn {
  background-color: lightgrey;
  height: 40px;
  width: 100px;
}
.v-spinner
{
/*	  font-size: 10px;
    width: 60px;
    height: 40px;*/
    /*margin: 25px auto;*/
    text-align: center;

}
.v-spinner .v-clip
{
    -webkit-animation: v-clipDelay 2s 0s infinite linear;
            animation: v-clipDelay 2s 0s infinite linear;
    -webkit-animation-fill-mode: both;
	          animation-fill-mode: both;
    display: inline-block;
}
@-webkit-keyframes v-clipDelay
{
    12.5% {
    transform: rotate(135deg);
  }
  25% {
    transform: rotate(270deg);
  }
  37.5% {
    transform: rotate(405deg);
  }
  50% {
    transform: rotate(540deg);
  }
  62.5% {
    transform: rotate(675deg);
  }
  75% {
    transform: rotate(810deg);
  }
  87.5% {
    transform: rotate(945deg);
  }
  to {
    transform: rotate(1080deg);
  }
}
@keyframes v-clipDelay
{
    12.5% {
    transform: rotate(135deg);
  }
  25% {
    transform: rotate(270deg);
  }
  37.5% {
    transform: rotate(405deg);
  }
  50% {
    transform: rotate(540deg);
  }
  62.5% {
    transform: rotate(675deg);
  }
  75% {
    transform: rotate(810deg);
  }
  87.5% {
    transform: rotate(945deg);
  }
  to {
    transform: rotate(1080deg);
  }
}
</style>


