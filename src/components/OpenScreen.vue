<template>
    <div id="open-screen">
      <div id="title">תעודת זהות<br /> פיקוד העורף</div>
      <div id="circle"></div>
      <img id="fingerPrint" alt="fingerPrint" src="@/assets/media/fingerPrint.png" />
      <div id="line"></div>
      <img id="logo" alt="logo" src="@/assets/media/logo.png" />
      <button id="btn" @click="nextPage"> התחלה לומדה </button>
    </div>
  </template>
   
  <script>
  
  export default {
    name: "open-screen",
    components: {
    },
    data() {
      return {
      }
    },
    mounted() {
        document.getElementById("logo").style.display="none";
      setTimeout(() => {
        document.getElementById("logo").style.display ="block";
        document.getElementById("logo").classList.add("animationShow")
      }, 2000);
    },
    methods: {
      nextPage() {
        this.$emit('next-page');
      }
    }
  };
  </script>
  
  <style scoped>
  @font-face {
    font-family: Karantina;
    src: url("../assets/fonts/Karantina-Regular.ttf");
  }
  
  body,
  html {
    margin: 0;
    padding: 0;
    height: 100%;
    overflow: hidden;
    font-family: "Karantina";
    direction: rtl;
    background-color: #d9cdd7;
  }
  
  #title {
    position: absolute;
    top: 29vh;
    right: 21vw;
    font-size: 16vmin;
    color: #3d405b;
    z-index: 2;
  }
  
  #circle{
    position: absolute;
    top: 1vh;
    right: 14vw;
    background-color: #f9f7eb;
    border-radius: 70%;
    width: 65vw;
    height: 98vh;
    z-index: 1;
  }

  #fingerPrint {
    position: absolute;
    top: 28vh;
    right: 53vw;
    width: 16vw;
    z-index: 2;
  }
  
  #line {
    position: absolute;
    top: 31vh;
    right: 53.3vw;
    border-top: 6px solid green;
    border-bottom: none;
    width: 15.5vw;
    animation: upAndDown 2s linear;
    z-index: 2;
  }
  
  @keyframes upAndDown {
  
    0%,
    100% {
      top: 30vh;
    }
  
    50% {
      top: 68vh;
    }
  }
  
  #logo {
    position: absolute;
    top: 23vh;
    right: 46vw;
    width: 30vw;
    z-index: 3;
  }
  
  #btn {
    position: absolute;
    top: 66vh;
    right: 28vw;
    width: 7vw;
    height: 5vh;
    font-size: 3vmin;
    font-family: Karantina;
    border-radius: 15px;
    border: 2px solid #e89024;
    color: #e89024;
    cursor: pointer;
    z-index: 2;
  }

  .animationShow{
    animation: opacityUp 1s ease-in-out;
  }

  @keyframes opacityUp {
  0% {
    opacity: 0;
  }

  100% {
    opacity: 1;
    display: block;
  }
}
  </style>