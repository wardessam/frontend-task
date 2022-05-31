
<template>

<div class="split left">
  <div class="centered">
   <div>
    <transition-group name="fade" tag="div">
      <div v-for="i in [currentIndex]" :key="i">
        <img :src="currentImg" />
        <span class="textImg">{{currentText}}</span>
      </div>
    </transition-group>
    <a class="prev" @click="prev" href="#">&#10094;</a>
    <a class="next" @click="next" href="#">&#10095;</a>
  </div>
  </div>
</div>

<div class="split right">
  <div class="centered">
   <img src="../assets/logo.png" class="logo"/>
   <div class="msglogin">Log in to Instabug</div>
  </div>
</div>

  
</template>

<script>
export default {
  name: "slider-login",
  data() {
    return {
      images: [
      "https://svgshare.com/i/hrA.svg",
      "https://svgshare.com/i/hrB.svg",
      "https://svgshare.com/i/hrV.svg"
      ],
       textunderImgs: [
      "Accelerate Your Entire Mobile Team Workflow",
      "The Most Comprehensive Bug Reporting Tool for Mobile Apps",
      "Secure Crash Reporting With Real-Time Alerts"
      ],
      timer: null,
      currentIndex: 0
    };
  },

  mounted: function() {
    this.startSlide();
  },

  methods: {
    startSlide: function() {
      this.timer = setInterval(this.next, 4000);
    },

    next: function() {
      this.currentIndex += 1;
    },
    prev: function() {
      this.currentIndex -= 1;
    }
  },

  computed: {
    currentImg: function() {
      return this.images[Math.abs(this.currentIndex) % this.images.length];
    },
     currentText: function() {
      return this.textunderImgs[Math.abs(this.currentIndex) % this.textunderImgs.length];
    }
  }
};
</script>
<style>
.split {
  height: 100%;
  width: 50%;
  position: fixed;
  z-index: 1;
  top: 0;
  overflow-x: hidden;
  padding-top: 20px;
}

.left {
  left: 0;
  background-color: darkblue;
}

.right {
  right: 0;
}

.textImg{
    color:white;
    font-size: larger;
}
.centered {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  text-align: center;
}
.fade-enter-active,
.fade-leave-active {
  transition: all 0.9s ease;
  overflow: hidden;
  visibility: visible;
  position: absolute;
  width:100%;
  opacity: 1;
}

.fade-enter,
.fade-leave-to {
  visibility: hidden;
  width:100%;
  opacity: 0;
}

img {
  width:40rem;
  background-color: darkblue;
}

.prev, .next {
  cursor: pointer;
  position: absolute;
  top: 40%;
  width: auto;
  padding: 16px;
  color: white;
  font-weight: bold;
  font-size: 18px;
  transition: 0.7s ease;
  border-radius: 0 4px 4px 0;
  text-decoration: none;
  user-select: none;
}

.next {
  right: 0;
}

.prev {
  left: 0;
}

.prev:hover, .next:hover {
  background-color: rgba(0,0,0,0.9);
}
.logo{
    width:20%;
    height:20%;
}
.msglogin{
    font-size: x-large;
    margin-top:10%
}
.google-btn {
  width: 184px;
  height: 42px;
  background-color:#4285f4 ;
  border-radius: 2px;
  box-shadow: 0 3px 4px 0 rgba(0,0,0,.25);
}
  .google-icon-wrapper {
    position: absolute;
    margin-top: 1px;
    margin-left: 1px;
    width: 40px;
    height: 40px;
    border-radius: 2px;
    background-color: white;
  }
  .google-icon {
    position: absolute;
    margin-top: 11px;
    margin-left: 11px;
    width: 18px;
    height: 18px;
  }
  .btn-text {
    float: right;
    margin: 11px 11px 0 0;
    color: white;
    font-size: 14px;
    letter-spacing: 0.2px;
    font-family: "Roboto";
  }
  


</style>