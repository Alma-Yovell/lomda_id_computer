<template>
    <div id="reception">
        <img id="register" alt="register" src="@/assets/media/register.png" />
        <div id="text">
            בלומדה זו תצרו את תעודת הזהות של פיקוד העורף ותוך כדי
            תלמדו מידע בסיסי וחשוב
        </div>
        <img id="arrow" class="animationLR" alt="arrow" src="@/assets/media/arrow.png" @click="nextPage" />
    </div>
</template>
  
<script>
export default {
    name: "reception",
    data() {
        return {
        };
    },
    methods: {
        nextPage() {
            document.getElementById("arrow").classList.remove("animationLR");
            document.getElementById("arrow").classList.add("opacityChange");
            setTimeout(() => {
                document.getElementById("arrow").style.display= "none";
            }, 500);

            document.getElementById("register").classList.add("goDown");
            document.getElementById("text").classList.add("goDown");

            setTimeout(() => {
                this.$emit("next-page");
            }, 2000);
        },
    },
};
</script>
  
<style scoped>

.opacityChange {
  animation: opChange 0.5s linear;
}

@keyframes opChange {
  0% {
    opacity: 1;
    left: 17vw; /* Add the original left position */
  }

  100% {
    opacity: 0;
    left: 17vw; /* Add the original left position */
  }
}

#register {
    position: absolute;
    top: 12.5vh;
    right: 0vw;
    width: 65vw;
}

#text {
    position: absolute;
    top: 27vh;
    right: 64vw;
    width: 30vw;
    font-size: 8vmin;
    text-align: center;
}

#arrow {
  position: absolute;
  top: 54vh;
  width: 8vw;
  cursor: pointer;
}

.animationLR {
    animation: leftAndRight 1s linear infinite;

}

@keyframes leftAndRight {

    0%,
    100% {
        left: 17vw;
    }

    50% {
        left: 17.5vw;
    }
}

.goDown {
    animation: animationDown 2s linear;
}


@keyframes animationDown {

    0% {
        top: 12.5vh;

    }

    100% {
        top: 100vh;
    }

    50% {
        top: 50vw;
    }
}
</style>