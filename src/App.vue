<template> 
<div class="host" >
<div class="three" ref="three" @wheel="handleScroll" @touchmove="handleScroll22">
  <div class="card">
    <h2 class="bai">网协干事工作证</h2>
    <div class="zqi aaa"><span class="zi">姓名</span><span class="you">{{ Worker[0].name }}</span></div><br>
    <div class="zqi"><span class="zi">性别</span><span class="you">{{ Worker[0].nn }}</span></div><br>
    <div class="zqi"><span class="zi">职位</span><span class="you">{{ Worker[0].work }}</span></div>
  </div>
</div>

 <div class="header" ref="one" @wheel="handleScroll1" @touchmove="handleScroll33">
  <div class="inner-header flex">
    <div class="yno">
        <div class="nnn"><div class="typed-out"><p class="kkk">是否准备好加入<br>网络协会 || ACM协会</p></div>
          <div class="bu">  
            <button class="ll1" @click="isHandle"> 准备好了</button><button class="ll2" @click="openDialog">我再想想</button>
            <dialog id="dog" ref="dog">
            <div class="win">
              <h2 class="pp">真的不来吗！</h2>
              <p class="jj">请慎重选择！</p>
              <br><br><br>
              <button @click="closeDialog" class="bb1">我来了</button>
              <button class="bb">不来了</button>
            </div>
          </dialog>
        </div>
      </div>
    </div>
  </div>
  <div>
      <!--
          xmlns:SVG命名看见URI
          viewBox:定义当前视口（viewbox）中绘制区域的位置大小
          preserveeAspectRatio：定义了绘制区域在视口中的对齐方式
          shape-rendering：定义了形状的渲染方式（如何呈现头像的锯齿效果）-->
      <svg class="waves" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"
          viewBox="0 24 150 28" preserveAspectRatio="none" shape-rendering="auto">
          <!-- 定义一个defs元素，用于存储各种元素的定义，可以被其他元素引用。
              在defs元素中定义了一个名为“gentle-wave”的路径元素，用于描述波浪形状
              改路径秒苏联一系列二次贝塞尔曲线的控制点坐标，从而实现了波浪形状 -->
          <defs>
              <path id="gentle-wave"
                  d="M-160 44c30 0 58-18 88-18s 58 18 88 18 58-18 88-18 58 18 88 18 v44h-352z" />
          </defs>
          <!-- 定义一个g元素，用于讲多个图形组合在一期，并应用一些样式
              在g元素中使用use元素多次引用了赚钱定义的名为gentle-wave的路径元素
              通过设置不同的x，y坐标和填充颜色，实现了波浪形状和渐变效果 -->
          <g class="parallax">
              <use xlink:href="#gentle-wave" x="48" y="0" fill="rgba(255,255,255,0.7)" />
              <use xlink:href="#gentle-wave" x="48" y="3" fill="rgba(255,255,255,0.5)" />
              <use xlink:href="#gentle-wave" x="48" y="5" fill="rgba(255,255,255,0.3)" />
              <use xlink:href="#gentle-wave" x="48" y="7" fill="#fff" />
          </g>
      </svg>
  </div>
</div>
<div class="content flex">
  <div class="nalogo"></div>
  <h2>网络协会 | ACM协会</h2>
  <div class="acmlogo"></div>
</div>
<div class="two" ref="two" @wheel="handleScroll2" @touchmove="handleScroll11">
  
  <div class="tt" >
    <h2 class="ooo">点击图片刷新</h2>
    <div :style="{ backgroundImage: 'url(' + currentImage + ')' }"  @click="changeImage" class="img">
  </div>


  
  

</div>
</div>
</div>
</template> 
<script>
import image1 from './img/1.jpg';
import image2 from './img/2.jpg';
import image3 from './img/3.jpg';
import image4 from './img/4.png';
import image5 from './img/5.jpg';
import image6 from './img/6.jpg';
import image7 from './img/7.jpg';
import image8 from './img/8.jpg';
import image9 from './img/9.png';

  export default { 
    
    data(){
      return{
      images:[
        image1,
        image2,
        image3,
        image4,
        image5,
        image6,
        image7,
        image8,
        image9,

      ],
      currentIndex: 0,
      isOpen: false,
      threeHeight:0,
      twoHight:0,
      isGetTop: true,
      cs:'sskskk',
      Worker: [{
          id:1,
          name:'陈广文',
          nn:'男',
          work:'会长'
        }]
    }
  },
  mounted() {
    window.addEventListener('scroll', this.isTop);
    setInterval(() => {
      this.threeHeight = this.$refs.three.offsetHeight;
      this.twoHeight = this.$refs.two.offsetHeight;
      console.log(`1元素高度为 ${this.threeHeight}px`);
      console.log(`2元素高度为 ${this.twoHeight}px`);
    }, 1000);
  },
  destroyed() {
    window.removeEventListener('scroll', this.isTop);
  },
  computed: {
    currentImage() {
      return this.images[this.currentIndex];
    }
  },
    methods: {
    isTop(){
      const divElement = this.$refs.one; // 替换为你的div元素的ref
      const divTop = divElement.getBoundingClientRect().top;

      if (divTop >= 0) {
        // 当div的顶端与窗口顶端重合时执行打印函数
        console.log('顶端与窗口顶端重合');
        this.isGetTop = true;
        // 在这里调用你的打印函数
      }
      else{
        this.isGetTop = false;
      }
    },
    isHandle(){
      this.isOpen = true;
      this.$refs.three.style.height = '100vh';
    },
    handleScroll1(event){
      if(this.isGetTop && this.isOpen && this.twoHight==0 && this.threeHeight==0){
        if(event.deltaY<0 ){
          console.log(666);
          this.$refs.three.style.height = '100vh';
          this.$refs.two.style.height = '0';
        }
        else{
          this.$refs.two.style.height = '100vh';
          this.$refs.three.style.height = '0';
        };
      }
    },
    handleScroll(event) {
      if(this.isOpen && this.isGetTop){
        // 在这里处理滚轮事件
        // event.deltaY 提供了滚轮滚动的距离信息
        console.log('滚动距离:', event.deltaY);
        if(event.deltaY<0 ){
          console.log(666);
          this.$refs.three.style.height = '100vh';
          this.$refs.two.style.height = '0';
        }
        else{
          this.$refs.three.style.height = '0';
        };
        // if(event.deltaY<0 && this.threeHeight==0){
        //   console.log(666);
        //   this.$refs.two.style.height = '0';
        // }
        // else{
        //   this.$refs.two.style.height = '100vh';
        // };
    }
    },
    handleScroll2(event) {
      if(this.isOpen && this.isGetTop ){
        // 在这里处理滚轮事件
        // event.deltaY 提供了滚轮滚动的距离信息
        console.log('滚动距离:', event.deltaY);
        // if(event.deltaY<0 && this.twoHight==0){
        //   console.log(666);
        //   this.$refs.three.style.height = '100vh';
        // }
        // else{
        //   this.$refs.three.style.height = '0';
        // };
        if(event.deltaY<0 ){
          console.log(666);
          this.$refs.two.style.height = '0';
        }
        else{
          this.$refs.two.style.height = '100vh';
          this.$refs.three.style.height = '0';
        };
    }
    },
    openDialog() {
      const dialogElement = this.$refs.dog; // 获取对话框元素
      dialogElement.showModal(); // 显示对话框
    },
    closeDialog() {
      const dialogElement = this.$refs.dog; // 获取对话框元素
      dialogElement.close(); // 关闭对话框
    },
    changeImage() {
      this.currentIndex = (this.currentIndex + 1) % this.images.length;
    },
    handleScroll11(event) {
      const touch = event.touches[0]; // 获取第一个触摸点的信息
      const deltaY = touch.pageY - this.startY; // 计算Y轴滑动的距离
      if(this.isOpen &&this.isGetTop){
      if (deltaY < 0) {
        // 向上滑动
        this.isScrollingUp = true;
        this.$refs.two.style.height = '100vh'; // 修改内部样式
      } else {
        // 向下滑动
        this.isScrollingUp = false;
        this.$refs.two.style.height = '0'; // 修改内部样式
      }
    }

      this.startY = touch.pageY; // 更新起始滑动位置
    },
    handleScroll22(event) {
      const touch = event.touches[0]; // 获取第一个触摸点的信息
      const deltaY = touch.pageY - this.startY; // 计算Y轴滑动的距离
      if(this.isOpen && this.isGetTop){
      if (deltaY < 0) {
        // 向上滑动
        this.isScrollingUp = true;
        this.$refs.three.style.height = '0'; // 修改内部样式
      } else {
        // 向下滑动
        this.isScrollingUp = false;
        this.$refs.three.style.height = '100vh'; // 修改内部样式
      }
    }
      this.startY = touch.pageY; // 更新起始滑动位置
    },
    handleScroll33(event) {
      const touch = event.touches[0]; // 获取第一个触摸点的信息
      const deltaY = touch.pageY - this.startY; // 计算Y轴滑动的距离
      if(this.isOpen && this.isGetTop){
      if (deltaY < 0) {
        // 向上滑动
        this.isScrollingUp = true;
        this.$refs.three.style.height = '0'; // 修改内部样式
        this.$refs.two.style.height = '100vh';
      } else {
        // 向下滑动
        this.isScrollingUp = false;
        this.$refs.three.style.height = '100vh'; // 修改内部样式
        this.$refs.two.style.height = '0';
      }
    }
      this.startY = touch.pageY; // 更新起始滑动位置
    },
    onTouchStart(event) {
      const touch = event.touches[0]; // 获取第一个触摸点的信息
      this.startY = touch.pageY; // 记录起始滑动位置
    }
  }
}
  
  </script> 
  <style>
  .host{
    position: relative;
  }
  .two{
    position: absolute;
    z-index: 1;
    width: 100vw;
    height: 0;
    bottom: 0;
    transition: all 2s;
    overflow: hidden;
  }

  
  /* .three{
    position: absolute;
    z-index: 1;
    width: 100vw;
    height: 0;
    background: blue;
  } */
  .three{
    position: absolute;
    height: 0;
    z-index: 1;
    width: 100vw;
    transition: all 2s;
    background: blue;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden;
    background: url(./img/join2.jpg);
    background-size: cover;
    object-fit: cover;
    background-position: center center;

  }
  .card{
    width: 80%;
    height: 70vh;
    background: rgba(255, 255, 255, 0.3);
    border-radius: 10px;
    box-shadow: 0 0 10px 5px rgba(0, 0, 0, 0.2);
    text-align: center;
  }
  .bai{
    color: #fff;
    margin-top: 50px;
    font-size: 40px;
    
  }
  .zqi{
    color: #fff;
    width: 300px;
    height: 40px;
    display: inline-block;
    margin-top: 20px;
  }
  .aaa{
    margin-top: 100px;
  }
  .zi{
    float: left;
  }
  .you{
    float: right;
    width: 200px;
    height: 50%;
    margin-right: 30px;
    border-bottom: 1px solid #fff;
  }
  .bu{
    
    width: 400px;
  }
    .ll1{
    float: left;
    margin-left: 20px;
    border: none;
    text-align: center;
    width: 120px;
    height: 70px;
    margin-top: 100px;
    color: white;
    font-size: 20px;
    font-weight: bolder;
    border-radius: 5px;
    background: rgba(255, 255, 255, 0.1);
    box-shadow: 
    2px 2px 4px rgba(0, 0, 0, 0.2);
  }

  .ll1:hover{
    background: rgba(255, 255, 255, 0.2);
    box-shadow: 
    4px 4px 8px rgba(0, 0, 0, 0.2);
  }
  .ll2{
    margin-right: 20px;
    float: right;
    border: none;
    text-align: center;
    width: 120px;
    height: 70px;
    margin-top: 100px;
    color: white;
    border-radius: 5px;
    background: rgba(255, 255, 255, 0.1);
    font-size: 20px;
    font-weight: bolder;
    box-shadow: 
    2px 2px 4px rgba(0, 0, 0, 0.2);
  }
  .ll2:hover{
    background: rgba(255, 255, 255, 0.2);
    box-shadow: 
    4px 4px 8px rgba(0, 0, 0, 0.2);
    
  }
h1 
{ font-weight: 300; 
letter-spacing: 2px; 
font-size: 48px; 
} 
p 
{ font-family: 'Lato', sans-serif;
letter-spacing: 1px; 
font-size: 30px; 
color: #333333; 
} 
.header { 
position: absolute;
position: relative;
text-align: center;
background: linear-gradient(60deg, rgba(84, 58, 183, 1) 0%, rgba(0, 172, 193, 1) 100%);
color: white; 
} 
.inner-header {
height: 65vh;
width: 100%; 
margin: 0; 
padding: 0; 
} .flex {
display: flex;
justify-content: center;
align-items: center; 
text-align: center; 
} 
.yno{ 
height: 300px; 
/* border: 3px solid black; */ /* background: rgba(255, 255, 255, 0.1); */ 
}
.waves { 
position: relative; 
width: 100%; 
height: 15vh; 
margin-bottom: -7px; 
min-height: 100px; 
max-height: 150px;
} 
.content {
position: relative; 
height: 20vh; 
text-align: center;
background-color: white; 
} 
.parallax>use { /* 使use元素执行move-forever动画 */ 
animation: move-forever 25s cubic-bezier(.55, .5, .45, .5) infinite;
}
.parallax>use:nth-child(1) {
/* 延迟2秒启动动画 */ animation-delay: -2s; 
/* 设置动画持续时间为7秒 */ animation-duration: 7s; 
}
.parallax>use:nth-child(2) {
animation-delay: -3s;
animation-duration: 10s;
}
.parallax>use:nth-child(3) {
animation-delay: -4s;
animation-duration: 13s;
}
.parallax>use:nth-child(4) {
animation-delay: -5s;
animation-duration: 20s;
}
@keyframes move-forever { 
0% { transform: translate3d(-90px, 0, 0);
}
100%
{ transform: translate3d(85px, 0, 0); }
}
@media (max-width: 768px) { 
.waves {
  height: 40px; 
  min-height: 40px; 
}
.content { 
  height: 30vh; 
} 
h1 { 
  font-size: 24px; 
} 
}
.nnn{ 
  display: inline-block; 
  margin-top: 80px; 
}
.kkk{ 
  color: #fff; 
  font-size: 3.5vh; 
}
.typed-out{ 
overflow: hidden; 
border-right: .15em solid orange;
white-space: nowrap; animation: typing 1.5s steps(20, end) forwards,
border-disappear .5s forwards 1s; font-size: 1.6rem; width: 0; 
}
@keyframes typing {
  from { width: 0 } to { width: 100% } 
}
@keyframes border-disappear {
  to { border-right: none } 
  }
#dog{
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  border-radius: 10px;
  width: 200px;
  height: 200px;
  background: rgba(255, 255, 255, 0.2);
  border: none;
}
#dog::backdrop{
  background: url(./img/xiu.jpg);
  background-color: white;
  object-fit: cover;
  background-position: center;
  background-size: contain;
  background-repeat: no-repeat;
  z-index: 33;
}
.pp{
  margin-top: 20px;
  margin-left: 20px;
}
.jj{
  margin-left: 10px;
  font-size: 10px;
}
.bb{
  background: rgb(232, 149, 98);
  margin-left: 20px;
  width: 50px;
  height: 26px;
    box-shadow: 
    4px 4px 8px rgba(0, 0, 0, 0.4);
    border: none;
}
.bb1{
  background: rgb(232, 149, 98);
  margin-right: 20px;
  width: 50px;
  height: 26px;
    box-shadow: 
    4px 4px 8px rgba(0, 0, 0, 0.4);
    border: none;
}
button{
  cursor: pointer;
}
.img{
  background-position: center;
  background-repeat: no-repeat;
  background-size: contain;
  width: 300px;
  height: 300px;
  float: bottom;
  z-index: 333;
}
.tt{
    background-image: linear-gradient(to right top, #e87096, #ff8278, #ffa159, #f2c648, #c8eb5b);
    width: 100vw;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    bottom: 0;
    text-align: center;
    flex-direction: column;
  }
.nalogo{
  background: url(./img/logo.jpg);
  float: left;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  background-size: 100%;
  margin-right: 20px;
}
.acmlogo{
  background: url(./img/acmlogo.jpg);
  float: right;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  background-size: 100%;
  margin-left: 20px;
}
.ooo{
  margin-bottom: 10px;
  
}
</style>

