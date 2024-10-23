<template>
  <div id="banner" class="w">
    <span class="iconfont" @click="preImage">&#xe618;</span>
    <span class="iconfont" @click="nextImage">&#xe617;</span>
    <div class="bd">
      <img v-bind:src="currentSrc" alt="">
    </div>

    <div class="dot">
      <ul>
        <li class="active"></li>
        <li></li>
        <li></li>
        <li></li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      sliderData: [
       './images/banner1.jpg', 
       './images/banner2.jpeg', 
       './images/banner3.jpg', 
       './images/banner4.jpg', 
      ],
      currentIndex: 0,
      currentSrc : './images/banner1.jpg',

    };
  },
  mounted() {
    this.startAutoPlay();
  },
  beforeUnmount() {
    this.stopAutoPlay();
  },
  methods: {
    startAutoPlay() {
      this.intervalId = setInterval(this.nextImage, 3000);
    }, 
    stopAutoPlay() {
      clearInterval(this.intervalId);
    },
    nextImage() {
      this.currentIndex = (this.currentIndex + 1) % this.sliderData.length;
      this.changeImage(this.currentIndex);
    },
    preImage() {
      this.currentIndex = (this.currentIndex - 1 + this.sliderData.length) % this.sliderData.length;
      this.changeImage(this.currentIndex);
    },
    changeImage(index) {
      this.currentSrc = this.sliderData[index];
      let lis = document.querySelectorAll('#banner .dot ul li');
      for (let i = 0; i < lis.length; i++) {
        if (i === this.currentIndex) {
          lis[i].classList.add('active');
        } else {
          lis[i].classList.remove('active');
        }
      }
    },
  }
}
</script>

<style scoped>
#banner {
  width: 80%;
  margin: 0 auto;
  margin-top: 60px;
  position: relative;
  display: flex;
  align-items: center;
}

#banner .bd {
  width: 100%;
  overflow: hidden;
  aspect-ratio: 16 / 9;
}

#banner .bd img {
  width: 100%;
  height: auto;
  transition: transform 0.5s ease-in-out;
}

#banner span {
  width: 40px;
  height: 60px;
  color: #fff;
  background-color: rgba(0, 0, 0, .2);
  font-size: 30px;
  border-radius: 10px;
  line-height: 60px;
  text-align: center;
  cursor: pointer;
}

#banner span:first-child {
  position: absolute;
  left: 0;
}

#banner span:nth-child(2) {
  position: absolute;
  right: 0;
}

#banner span:hover {
  background-color: rgba(0, 0, 0, .3);
}

#banner .dot {
  position: absolute;
  bottom: 0;
}

#banner .dot ul {
  display: flex;
  margin-bottom: 20px;
  margin-left: 20px;
}

#banner .dot ul li {
  margin: 5px;
  width: 10px;
  height: 10px;
  border-radius: 5px;
  background-color: #fff;
}


#banner .dot li:hover,
#banner .dot li.active {
  transform: scale(1.2);
}
</style>