<template>
    <div id="hand-id">
        <img id="handWithId" alt="handWithId" src="@/assets/media/handWithId.png" />
        <div id="text">
            לחצו על התעודת זהות והתחילו ללמוד
        </div>
        <div id="idDiv" @click="nextPage"></div>
    </div>
</template>
   
<script>
export default {
    name: "hand-id",
    components: {},
    data() {
        return {
        }
    },
    mounted() {
        document.getElementById("handWithId").classList.add("opacityChange");
        document.getElementById("text").classList.add("opacityChange");
    },
    methods: {
        nextPage() {
            this.$emit('next-page');
        }
    }
};
</script>
  
<style scoped>
#handWithId {
    position: absolute;
    right: 46vw;
    width: 53vw;
}

.opacityChange{
    animation: opChange 1s linear;
}

@keyframes opChange {
    0%
    {
        opacity: 0.2;
    }
    100% {
        opacity: 1;
    }
    50% {
        opacity: 0.5;
    }
}


#text {
    position: absolute;
    top: 35vh;
    right: -1vw;
    width: 46vw;
    font-size: 8vmin;
    text-align: center;
}

#idDiv {
    position: absolute;
    top: 25vh;
    right: 64vw;
    width: 25vw;
    height: 28vh;
    border-radius: 36px;
    background-color: transparent;
    cursor: pointer;
}
</style>