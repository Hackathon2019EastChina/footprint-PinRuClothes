<template>
    <div class="ribbon" v-if="ribbonEnabled"><a href="" v-text="$t('global.ribbon.' + ribbonEnv)">{{ribbonEnv}}</a></div>
</template>

<script lang="ts" src="./ribbon.component.ts">
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    /* ==========================================================================
Developement Ribbon
========================================================================== */
    .ribbon {
        background-color: rgba(170, 0, 0, 0);
        left: 2em;
        overflow: hidden;
        position: absolute;
        top: 50px;
        white-space: nowrap;
        width: 90em;
        z-index: 9999;
        pointer-events: none;
        opacity: 0.75;
    }

    .ribbon a { 
        color: #fff;
        display: block;
        font-weight: 400;
        margin: 1px 0;
        padding: 10px 50px;
        text-align: center;
        text-decoration: none;
        text-shadow: 0 0 5px rgb(32, 4, 4);
        pointer-events: none;
    }

</style>
