<template>
	<div>
        <div class="currentscore-container">
            <p>{{score}}</p>
            <p>Current Score</p>
        </div>
        <p style="text-align: center" class="timeout"><span class="white">Time</br></span> RAN OUT!
        <p style="text-align: center">You lost 1 Life</p>
        <uiButton class="btn4" v-bind:onClick="onNextQuestion" title="Next Question"></uiButton>  
    </div>
</template>

<style scoped lang="sass">

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
            margin-bottom: 8px
            &:first-child
                font: 
                    size: 32px
                    family: "Roboto Slab"

    .btn4
        position: absolute
        bottom: 24px
        left: 50%
        transform: translateX(-50%)
        display: block

    .timeout
        /* Sorry, WRONG! */

        position: absolute;
        width: 237px;
        height: 98px;
        left: 69px;
        top: 164px;

        font-family: Roboto Slab;
        font-style: normal;
        font-weight: bold;
        line-height: normal;
        font-size: 48px;
        text-align: center;
        color: #ED3964
        text-shadow: 0px 0px 4px rgba(0, 0, 0, 0.25);

    .white
        color: #FFFFFF;
        font-size: 32px
        font-weight: normal;


</style>


<script>
import { Event } from "../event.js";
import uiButton from "./ui_elements/Button.vue";
export default {
    name: "timeover",
    components: { uiButton },
    data() {
        return {
            name: "timeover"
        };
    },
    props: ["onNextQuestion", "onEndGame", "score"]
};
</script>

