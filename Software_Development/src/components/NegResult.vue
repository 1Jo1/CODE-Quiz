<template>
	<div class="container-result">
        <div class="currentscore-container">
            <p>{{score}}</p>
            <p>Current Score</p>
        </div>
        <p style="text-align: center" class="incorrect"><span class="white">{{currentText}}</br></span> WRONG!</p>
        <div class="container-hearts">
            <i v-for="n in lifes" ref="heart" class="fa fa-heart heart"></i>
            <i v-for="n in (3 - lifes)" ref="heart" class="fa fa-heart heart disabled"></i>
        </div>
        <uiButton class="btn3" v-bind:onClick="onNextQuestion" title="Next Question"></uiButton>
    </div>
</template>



<script>
import { Event } from "../event.js";
import uiButton from "./ui_elements/Button.vue";

export default {
    props: ["onNextQuestion", "onEndGame", "lifes", "score"],
    name: "negresult",
    components: { uiButton },
    data() {
        return {
            name: "negresult",
            texts: [
                "Sorry,",
                "Nope, nope, nope",
                "Try again",
                "You fool",
                "Really?",
                "Try harder!",
                "So close!",
                "Dude, come on ..."
            ],
            currentText: ""
        };
    },
    mounted: function() {
        const toAnimate = this.lifes;
        console.log(toAnimate);
        console.log(this.$refs.heart);
        this.$refs.heart[toAnimate].classList.add("animate");

        const rand = Math.floor(Math.random() * this.texts.length);
        console.log(rand);
        this.currentText = this.texts[rand];
    }
};
</script>

<style lang="sass">

    .currentscore-container
        position: absolute
        top: 48px
        width: 100%
        color: #EDEDEE
        text-align: center
        font: 
            size: 16px
            family: "Source Sans Pro"
        p
            margin-bottom: 12px
            &:first-child
                font: 
                    size: 32px
                    family: "Roboto Slab"

    .container-result
        height: calc(100vh - 58px - 24px)
        display: flex
        justify-content: center
        flex-direction: column

    .container-hearts
        display: flex
        justify-content: space-around
        padding-left: 48px
        padding-right: 48px
        animation: fadeIn
        animation-duration: 0.3s
        opacity: 0
        animation-fill-mode: forwards

    .heart
        font-size: 72px
        color: #E42F5A        

        &.disabled
            color: #565656

        &.animate
            animation: heart
            animation-duration: 0.45s
            animation-delay: 0.8s
            animation-timing-function: easeInOutQuad
            color: #E42F5A 
            animation-fill-mode: forwards
    
    @keyframes fadeIn
        0%
            opacity: 0
        100%
            opacity: 1 
    
    @keyframes heart
        0%
            color: #E42F5A
            transform: scale(1)
        30%
            transform: scale(1.2)
        100%
            color: #565656  
            transform: scale(1)
            
    .btn3
        position: absolute
        bottom: 24px
        left: 50%
        transform: translateX(-50%)
        display: block

    .white
        color: #FFFFFF;
        font-size: 28px
        font-weight: normal;
    
    .incorrect
        animation: scaleIn
        animation-duration: 0.4s
        animation-easing: easeInOutQuad

        margin-bottom: 48px

        font-family: Roboto Slab;
        font-style: normal;
        font-weight: bold;
        line-height: normal;
        font-size: 48px;
        text-align: center;

        color: #ED3964
        text-shadow: 0px 0px 4px rgba(0, 0, 0, 0.25);

    @keyframes scaleIn
        0%
            transform: scale(3)
        70%
            transform: scale(0.85)
        100%
            transform: scale(1)

</style>