<template>
<div id="bg">
    <div class="home row">
        <div class="col-md-9">
            <br>
            <h1 class="display-4">&nbsp;&nbsp;&nbsp;渡洋之行</h1>
            <br>
            <p class="display-3">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;你的梦想，从这里开始：the journey to the other side</p>
            <b-container class="bv-example-row">
            <b-row align-h="center">
            <b-col>
                <hr width=135%>
                    <b-carousel
                        id="carousel-1"
                        v-model="slide"
                        :interval="4000"
                        controls
                        indicators
                        background="#ababab"
                        img-width="1024"
                        img-height="480"
                        style="text-shadow: 1px 1px 2px #333;"
                        @sliding-start="onSlideStart"
                        @sliding-end="onSlideEnd"
                        >
                        <!-- Text slides with image -->
                        <b-carousel-slide
                            caption="First slide"
                            text="Nulla vitae elit libero, a pharetra augue mollis interdum."
                            img-src="https://picsum.photos/1024/480/?image=52"
                        ></b-carousel-slide>

                        <!-- Slides with custom text -->
                        <b-carousel-slide img-src="https://picsum.photos/1024/480/?image=54">
                            <h1>Hello world!</h1>
                        </b-carousel-slide>

                        <!-- Slides with image only -->
                        <b-carousel-slide img-src="https://picsum.photos/1024/480/?image=58"></b-carousel-slide>

                        <!-- Slides with img slot -->
                        <!-- Note the classes .d-block and .img-fluid to prevent browser default image alignment -->
                        <b-carousel-slide>
                            <template v-slot:img>
                            <img
                                class="d-block img-fluid w-100"
                                width="1024"
                                height="480"
                                src="https://picsum.photos/1024/480/?image=55"
                                alt="image slot"
                            >
                            </template>
                        </b-carousel-slide>

                        <!-- Slide with blank fluid image to maintain slide aspect ratio -->
                        <b-carousel-slide caption="Blank Image" img-blank img-alt="Blank image">
                            <p>
                            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse eros felis, tincidunt
                            a tincidunt eget, convallis vel est. Ut pellentesque ut lacus vel interdum.
                            </p>
                        </b-carousel-slide>
                        </b-carousel>
                    <hr width=135%>
                </b-col>
            </b-row>
            </b-container>
        </div>
    </div>
    <br><br>
    <div class="home row">
        <div class="col-md-4">
            <h3 class="display-9">申请</h3>
            <hr>
            <ul>
                <li><a href="/apply/experience" target="_blank" rel="noopener" >MSCS@CMU项目申请经验</a></li>
                <li><a href="/apply/experience" target="_blank" rel="noopener" >Meng@UCB,一年制meng是否值得读</a></li>
                <li><a href="/apply/experience" target="_blank" rel="noopener" >东海岸与西海岸，不仅是时区差异</a></li>
                <li><a href="/apply/experience" target="_blank" rel="noopener" >19fall CSphD申请感想</a></li>
                <li><a href="http://127.0.0.1:5000/" target="_blank" rel="noopener">测试你的申请成功几率</a></li>
            </ul>
        </div>
        <div class="col-md-4">
            <h3 class="display-9">院校</h3>
            <hr>
            <ul>
                <li><a href="/apply/university" target="_blank" rel="noopener" >院校巡礼:Stanford</a></li>
                <li><a href="/apply/university" target="_blank" rel="noopener" >UCBerkeley申请情况分析</a></li>
                <li><a href="/apply/university" target="_blank" rel="noopener" >CS@CMU项目介绍与近年数据</a></li>
                <li><a href="/apply/university" target="_blank" rel="noopener" >2020MIT金工申请前景</a></li>
                <li><a href="http://127.0.0.1:5000/" target="_blank" rel="noopener" >测试你的申请成功几率</a></li>
            </ul>
        </div>
        <div class="col-md-4">
            <h3 class="display-9">定位</h3>
            <hr>
            <ul>
                <li><a href="/apply/consult" target="_blank" rel="noopener" >CS@NJU 4.6/5.0+110+330 2020US选校</a></li>
                <li><a href="/apply/consult" target="_blank" rel="noopener" >Top2 111+333 两段科研经历</a></li>
                <li><a href="/apply/consult" target="_blank" rel="noopener" >SE@NJU 4.65/5 一般TOEFL,gre 一篇sci二区</a></li>
                <li><a href="/apply/consult" target="_blank" rel="noopener" >Top2 3.7/4 MSRA实习+Upenn暑研</a></li>
                <li><a href="http://127.0.0.1:5000/" target="_blank" rel="noopener" >测试你的申请成功几率</a></li>
            </ul>
        </div>
    </div>
</div>
</template>

<script lang="ts" src="./apply.component.ts">
    export default {
        data() {
        return {
            slide: 0,
            sliding: null
        }
        },
        methods: {
        onSlideStart(slide) {
            this.sliding = true
        },
        onSlideEnd(slide) {
            this.sliding = false
        }
        }
    }
</script>

<style scoped>
#carousel-1{
    margin:0 0 0 2%;
    height: 90%;
    width: 130%;
}

#bg{width: 100%;
    height: 100%;
    position: relative;
    background-color: rgba(236, 246, 252, 0.87)}

.display-4{
    font-weight:normal;
}

.display-3{
    font-size:20px;
}

.display-9{
    font-weight:normal;
}
</style>