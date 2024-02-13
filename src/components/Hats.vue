<template>
    <div id="hats">
        <div id="divText">
            הסבר הסבר הסבר הסבר הסבר הסבר הסבר הסבר הסבר הסבר הסבר הסבר הסבר הסבר הסבר הסבר הסבר הסבר הסבר<br /><br />
            לחצו על הכובע המסומן כדי ללמוד על כל תפקוד יותר. רק לאחר שתלמדו על שלושת התפקודים תוכלו להמשיך בלומדה
        </div>
        <img class="hats" id="hat1" alt="hat1" src="@/assets/media/hat1.png" @click="showExpalntion" />
        <div v-if="show" class="textDiv">
            <button id="nextBtn" @click="closeExpalntion"> הבנתי </button>
        </div>
        <img class="hats" id="hat2" src="@/assets/media/disableHat.png" />
        <img class="hats" id="hat3" src="@/assets/media/disableHat.png" />
        <button v-if="counter === 3" id="doneBtn" @click="returnPage">סיימתי</button>
    </div>
</template>
   
<script>
export default {
    name: "hats",
    components: {},
    data() {
        return {
            counter: 0,
            show: false,
        }
    },
    methods: {
        returnPage() {
            this.$emit('return-main');
        },
        showExpalntion() {
            this.show = true;
        },
        closeExpalntion() {
            this.show = false;
            this.counter++;
            if (this.counter === 1) {
                document.getElementById("hat2").src = require('@/assets/media/hat2.png');
                document.getElementById("hat2").style.cursor = 'pointer';
                document.getElementById("hat2").addEventListener("click", () => this.showExpalntion());
            }
            if (this.counter === 2) {
                document.getElementById("hat3").src = require('@/assets/media/hat3.png');
                document.getElementById("hat3").style.cursor = 'pointer';
                document.getElementById("hat3").addEventListener("click", () => this.showExpalntion());
            }
        }
    }
};
</script>
  
<style scoped>
#hats {
    direction: rtl;
    height: 100vh;
    width: 100vw;
    background-image: url('../assets/media/background.png');
    background-size: 100% 100%;
    background-repeat: no-repeat;
}

#divText {
    position: absolute;
    top: 0vh;
    right: 0vw;
    height: 100vh;
    width: 20vw;
    background-color: rgba(83, 80, 80, 0.692);
    z-index: 1;
    color: white;
    padding-top: 28vh;
    padding-left: 3vw;
    padding-right: 3vw;
    text-align: center;
    font-size: 5vmin;
}

.hats {
    position: absolute;
}

#hat1 {
    top: 30vh;
    left: 24vh;
    cursor: pointer;
}

#hat2 {
    top: 30vh;
    left: 68vh;
}

#hat3 {
    top: 30vh;
    left: 111vh;
}

.textDiv {
    position: absolute;
    width: 63vw;
    height: 60vh;
    top: 22vh;
    left: 7vw;
    background-color: #efefeff2;
    border: 2px solid #aba79e;
    z-index: 2;
    border-radius: 20px;
}

#nextBtn {
    position: absolute;
    width: 9vw;
    height: 5vh;
    top: 50vh;
    left: 27vw;
    background-color: #f1d19b;
    border: 2px solid #5c4308;
    border-radius: 14px;
    font-size: 3vmin;
    font-family: Karantina;
    cursor: pointer;
}

#doneBtn{
    position: absolute;
    width: 9vw;
    height: 5vh;
    top: 78vh;
    left: 34vw;
    background-color: #85827c;
    border: 2px solid #ffffff;
    border-radius: 14px;
    font-size: 3vmin;
    color: white;
    font-family: Karantina;
    cursor: pointer;
}
</style>