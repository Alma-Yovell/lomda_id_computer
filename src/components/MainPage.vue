<template>
    <div id="main-page">

        <div v-if="mainPage">
            <img id="collegeLogo" alt="collegeLogo" src="@/assets/media/collegeLogo.png" />

            <div id="navBarDiv">
                <div id="navBar"></div>
                <div id="container">
                    <!-- <div class="header" v-for="(name, index) in arrNavBar" :key="index" :id="`name${index}`">
            {{ name }}
        </div> -->
                    <div class="circle" v-for="index in 9" :key="`circle${index}`" :id="`circle${index}`"
                        @mouseover="showHeader" @mouseout="hideHeader"></div>
                </div>


                <div id="idCard">
                    <div id="imgDiv"></div>
                    <div class="text " id="lastName"> <b>שם משפחה:</b> העורף </div>
                    <div class="text " id="firstName"> <b>שם פרטי:</b> פיקוד </div>
                    <div class="text" id="birthDate"> תאריך לידה: </div>
                    <div class="text" id="date"> תאריך הנפקה: </div>
                    <div class="text" id="expiration"> תוקף: </div>
                    <div id="numbers"> 0000000000000 </div>
                    <div id="idNumbers"> 000000000 </div>
                    <div id="chip"> </div>
                </div>

            </div>
        </div>

        <hats v-if="numPage === 1" @return-main="returnMain"></hats>

    </div>
</template>
  
<script>
import Hats from "@/components/Hats.vue";
export default {
    name: "main-page",
    components: {
        Hats
    },
    data() {
        return {
            mainPage: true,
            numPage: 0,
            showName: false,
            arrNavBar: ["תפקודי פקער", "תשתית חוקית ", 'מבנה פקע"ר+ מבנה פקע"ר בחירום ', 'מאמץ ומשימות פקע"ר ', 'מחוזות', 'סד"כ פקע"ר', 'מערכים לאומיים ', 'תרגול מסכם'],
        };
    },
    mounted() {
        document.getElementById("imgDiv").addEventListener("click", this.nextPage);
        document.getElementById("imgDiv").classList.add("clickHere");
    },
    methods: {
        nextPage() {
            this.mainPage = false;
            this.numPage++;
        },
        returnMain() {
            this.mainPage = true;
            this.numPage++;
            if (this.numPage === 2) {
                const imgDiv = document.getElementById("imgDiv");
                if (imgDiv) {
                    imgDiv.removeEventListener("click", this.nextPage);
                    imgDiv.classList.remove("clickHere");
                }
                document.getElementById("lastName").classList.add("clickHere");
            }
        },
        showHeader(event) {
            let numCircle = event.currentTarget.id.substring(6);
            for (let i = 0; i < this.arrNavBar.length; i++) {
                if (i == numCircle) {
                    document.getElementById(`name${numCircle}`).style.display = "block";
                }
            }
        },
        hideHeader(event) {
            let numCircle = event.currentTarget.id.substring(6);
            for (let i = 0; i < this.arrNavBar.length; i++) {
                if (i == numCircle) {
                    document.getElementById(`name${numCircle}`).style.display = "none";
                }
            }
        }
    }
};
</script>
  
<style scoped>
#main-page {
    direction: rtl;
    height: 100vh;
    width: 100vw;
    background-image: url('../assets/media/background.png');
    background-size: 100% 100%;
    background-repeat: no-repeat;
}

#imgLogo {
    z-index: 3;
}

#collegeLogo {
    position: absolute;
    top: 2vh;
    width: 7vw;
    right: 1vw;
}

#idCard {
    position: absolute;
    top: 18vh;
    left: 23vw;
    width: 62vw;
    height: 64vh;
    border-radius: 57px;
    border: 3px solid #d4dce3;
    background-color: aliceblue;
}

#navBar {
    position: absolute;
    top: 5vh;
    left: 2vw;
    width: 0.3vw;
    height: 89vh;
    background-color: black;
}

.circle {
    border-radius: 84px;
    background-color: black;
    width: 1vw;
    height: 2vh;
    margin-bottom: 1vh;
    transition: transform 0.2s ease-in-out;

    &:hover {
        transform: scale(1.6);
        cursor: pointer;
    }
}

.header {
    position: relative;
    position: relative;
    top: 2vh;
    left: 10vw;
    margin: 2vh;
    display: block;
}

#container {
    display: flex;
    flex-wrap: wrap;
    flex-direction: column;
    height: 90vh;
    position: absolute;
    top: 5vh;
    left: 1.6vw;
    height: 90vh;
    justify-content: space-between;
}


.text {
    font-size: 4.5vmin;
    position: absolute;
    cursor: pointer;
}

#imgDiv {
    top: 12vh;
    left: 45.2vw;
    width: 15vw;
    position: absolute;
    height: 30vh;
    background-color: #e6edf3;
    border-radius: 40px;
    cursor: pointer;
    z-index: 2;
}

#lastName {
    top: 12vh;
    left: 34vw;
}

#firstName {
    top: 20vh;
    left: 35.6vw;
}

#birthDate {
    top: 28vh;
    left: 37.4vw;
    font-weight: bold;
}

#date {
    top: 36vh;
    left: 36.8vw;
    font-weight: bold;
}

#expiration {
    top: 44vh;
    left: 41vw;
    font-weight: bold;
}

#numbers {
    top: 48vh;
    left: 3vw;
    width: 16vw;
    position: absolute;
    height: 6vh;
    background-color: #f8fcff;
    border-radius: 73%;
    color: #e1eaf3;
    text-align: center;
    font-size: 3vmin;
    padding-top: 2vh;
    cursor: pointer;

}

#idNumbers {
    position: absolute;
    top: 46vh;
    left: 52vw;
    color: #cad0d6;
    font-size: 3vmin;
    cursor: pointer;

}

#chip {
    top: 12vh;
    left: 8vw;
    width: 7vw;
    position: absolute;
    height: 12vh;
    background-color: #f1ede9;
    border-radius: 29px;
    cursor: pointer;

}

.clickHere {
    animation: click 1s linear infinite;
}

@keyframes click {

    0%,
    100% {
        transform: scale(1);
        border: 3px solid rgb(247, 247, 155);
    }

    50% {
        transform: scale(1.08);
        border: 3px solid rgb(247, 247, 155);
    }
}
</style>