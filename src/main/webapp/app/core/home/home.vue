<template>
    <div id="bg">
    <div class="home row">
        <div class="col-md-10">
            <br>
            <h1 class="display-4">&nbsp;&nbsp;&nbsp;WELCOME TO 行迹!</h1>
            <br>
            <p class="display-3">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;欢迎在这里，成为最好的你自己：be the best of yourself</p>

            <div id="login">
                <div class="alert alert-success" v-if="authenticated">
                    <span v-if="username" v-text="$t('home.logged.message', { 'username': username})"> "{&nbsp;&nbsp;&nbsp;{username}}"</span>
                </div>
                <div class="alert alert-warning" v-if="!authenticated">
                    <span v-text="$t('global.messages.info.authenticated.prefix')">If you want to </span>
                    <a class="alert-link" v-on:click="openLogin()" v-text="$t('global.messages.info.authenticated.link')">sign in</a><span v-html="$t('global.messages.info.authenticated.suffix')">, you can try the default accounts:<br/>- Administrator (login="admin" and password="admin") <br/>- User (login="user" and password="user").</span>
                </div>
                <div class="alert alert-warning" v-if="!authenticated">
                    <span v-text="$t('global.messages.info.register.noaccount')">You don't have an account yet?</span>&nbsp;
                    <router-link class="alert-link" to="/register" v-text="$t('global.messages.info.register.link')">Register a new account</router-link>
                </div>
            </div>

            <b-container class="bv-example-row">
            <b-row align-h="center">
            <b-col>
                <hr width=120%>
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
                        <b-carousel-slide caption="First slide" img-src="https://picsum.photos/1024/480/?image=10">
                        </b-carousel-slide>
                        </b-carousel>
                        <br><br><br><br>
                    <hr width=120%>
                </b-col>
            </b-row>
            <b-row>
            <p class="display-6">&nbsp;&nbsp;&nbsp;· 若你想要领略这个世界的广度，不妨到</p><b-link to="/apply" id="link" class="display-5">渡洋之行</b-link><p class="display-5">看看</p>
            <p class="display-6">&nbsp;&nbsp;&nbsp;· 若你想要探索这片土地的深度，欢迎来</p><b-link href="../../domestic" id="link" class="display-5">前行之迹</b-link><p class="display-5">看看</p>
            </b-row>
            </b-container>
        </div>
    </div>

    <footer id="footer" class="bg-white py-5 font-size-14">
    <div class="container">
        <div class="row">
            <dl class="col-4 col-md-2">
                <dt class="h6">关于我们</dt>
                                <dd class="my-1"><a class="text-secondary" href="/lives/edu?tag=java&amp;sort=hottest&amp;utm_source=sf-footer" target="_blank">来自南大软件学院</a></dd>
                                <dd class="my-1"><a class="text-secondary" href="/lives/edu?tag=php&amp;sort=hottest&amp;utm_source=sf-footer" target="_blank">做新时代007的程序员</a></dd>
                                <dd class="my-1"><a class="text-secondary" href="/lives/edu?tag=python&amp;sort=hottest&amp;utm_source=sf-footer" target="_blank">Azure部署：JY</a></dd>
                                <dd class="my-1"><a class="text-secondary" href="/lives/edu?category=1&amp;sort=hottest&amp;utm_source=sf-footer" target="_blank">前端开发：LGL</a></dd>
                                <dd class="my-1"><a class="text-secondary" href="/lives/study?category=3&amp;sort=hottest&amp;utm_source=sf-footer" target="_blank">后端开发：LJJ</a></dd>
            </dl>
            <dl class="col-4 col-md-2">
            </dl>

            <dl class="col-6 col-md-2 ">
            </dl>

            <dl class="col-4 col-md-2">
                <dt class="h6">合作</dt>
                                <dd class="my-1"><a class="text-secondary" href="https://about.segmentfault.com/?utm_source=sf-footer" target="_blank">加入我们</a></dd>
                                <dd class="my-1"><a class="text-secondary" href="https://business.segmentfault.com/ads?utm_source=sf-footer" target="_blank">创建分享社区</a></dd>
                                <dd class="my-1"><a class="text-secondary" href="/groups?tab=jobs&amp;utm_source=sf-footer" target="_blank">为自己努力</a></dd>
                                <dd class="my-1"><a class="text-secondary" href="/lives/apply?utm_source=sf-footer" target="_blank">为一代人的梦努力</a></dd>
                                <dd class="my-1"><a class="text-secondary" href="https://about.segmentfault.com/contact.html?utm_source=sf-footer" target="_blank">Hack For Better Life</a></dd>
                            </dl>

            <dl class="col-2 col-md-2">
            </dl>

            <dl class="col-4 col-md-2" >
            </dl>
        </div>
        <hr class="mt-2 mb-4">
        <div class="row">
            <div class="col-md-8">
                <div class="text-secondary">
                    <p class="mb-1">Copyright © 2019 Pinru's Clothes. 当前呈现版本 1.0.0</p>
                    <p class="mb-1">
                        "我的代码怎么穿着品如的衣服"版权所有
                    </p>
                </div>
            </div>
            <div class="col-md-4 text-right">
                <div class="shareContent ">
                <a class="share_weixin" data-share="weixin" href="javascript:;" data-original-title="" title=""><svg class="svg-inline--fa fa-weixin fa-w-18 fa-fw" aria-hidden="true" focusable="false" data-prefix="fab" data-icon="weixin" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 576 512" data-fa-i2svg=""><path fill="currentColor" d="M385.2 167.6c6.4 0 12.6.3 18.8 1.1C387.4 90.3 303.3 32 207.7 32 100.5 32 13 104.8 13 197.4c0 53.4 29.3 97.5 77.9 131.6l-19.3 58.6 68-34.1c24.4 4.8 43.8 9.7 68.2 9.7 6.2 0 12.1-.3 18.3-.8-4-12.9-6.2-26.6-6.2-40.8-.1-84.9 72.9-154 165.3-154zm-104.5-52.9c14.5 0 24.2 9.7 24.2 24.4 0 14.5-9.7 24.2-24.2 24.2-14.8 0-29.3-9.7-29.3-24.2.1-14.7 14.6-24.4 29.3-24.4zm-136.4 48.6c-14.5 0-29.3-9.7-29.3-24.2 0-14.8 14.8-24.4 29.3-24.4 14.8 0 24.4 9.7 24.4 24.4 0 14.6-9.6 24.2-24.4 24.2zM563 319.4c0-77.9-77.9-141.3-165.4-141.3-92.7 0-165.4 63.4-165.4 141.3S305 460.7 397.6 460.7c19.3 0 38.9-5.1 58.6-9.9l53.4 29.3-14.8-48.6C534 402.1 563 363.2 563 319.4zm-219.1-24.5c-9.7 0-19.3-9.7-19.3-19.6 0-9.7 9.7-19.3 19.3-19.3 14.8 0 24.4 9.7 24.4 19.3 0 10-9.7 19.6-24.4 19.6zm107.1 0c-9.7 0-19.3-9.7-19.3-19.6 0-9.7 9.7-19.3 19.3-19.3 14.5 0 24.4 9.7 24.4 19.3.1 10-9.9 19.6-24.4 19.6z"></path></svg><!-- <i class="fab fa-weixin fa-fw"></i> --> </a><a class="share_weibo" data-share="weibo" href="http://weibo.com/segmentfault" target="_blank"><svg class="svg-inline--fa fa-weibo fa-w-16 fa-fw" aria-hidden="true" focusable="false" data-prefix="fab" data-icon="weibo" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512" data-fa-i2svg=""><path fill="currentColor" d="M407 177.6c7.6-24-13.4-46.8-37.4-41.7-22 4.8-28.8-28.1-7.1-32.8 50.1-10.9 92.3 37.1 76.5 84.8-6.8 21.2-38.8 10.8-32-10.3zM214.8 446.7C108.5 446.7 0 395.3 0 310.4c0-44.3 28-95.4 76.3-143.7C176 67 279.5 65.8 249.9 161c-4 13.1 12.3 5.7 12.3 6 79.5-33.6 140.5-16.8 114 51.4-3.7 9.4 1.1 10.9 8.3 13.1 135.7 42.3 34.8 215.2-169.7 215.2zm143.7-146.3c-5.4-55.7-78.5-94-163.4-85.7-84.8 8.6-148.8 60.3-143.4 116s78.5 94 163.4 85.7c84.8-8.6 148.8-60.3 143.4-116zM347.9 35.1c-25.9 5.6-16.8 43.7 8.3 38.3 72.3-15.2 134.8 52.8 111.7 124-7.4 24.2 29.1 37 37.4 12 31.9-99.8-55.1-195.9-157.4-174.3zm-78.5 311c-17.1 38.8-66.8 60-109.1 46.3-40.8-13.1-58-53.4-40.3-89.7 17.7-35.4 63.1-55.4 103.4-45.1 42 10.8 63.1 50.2 46 88.5zm-86.3-30c-12.9-5.4-30 .3-38 12.9-8.3 12.9-4.3 28 8.6 34 13.1 6 30.8.3 39.1-12.9 8-13.1 3.7-28.3-9.7-34zm32.6-13.4c-5.1-1.7-11.4.6-14.3 5.4-2.9 5.1-1.4 10.6 3.7 12.9 5.1 2 11.7-.3 14.6-5.4 2.8-5.2 1.1-10.9-4-12.9z"></path></svg><!-- <i class="fab fa-weibo fa-fw"></i> --> </a><a class="share_github" data-share="github" href="https://github.com/SegmentFault" target="_blank"><svg class="svg-inline--fa fa-github fa-w-16 fa-fw" aria-hidden="true" focusable="false" data-prefix="fab" data-icon="github" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 496 512" data-fa-i2svg=""><path fill="currentColor" d="M165.9 397.4c0 2-2.3 3.6-5.2 3.6-3.3.3-5.6-1.3-5.6-3.6 0-2 2.3-3.6 5.2-3.6 3-.3 5.6 1.3 5.6 3.6zm-31.1-4.5c-.7 2 1.3 4.3 4.3 4.9 2.6 1 5.6 0 6.2-2s-1.3-4.3-4.3-5.2c-2.6-.7-5.5.3-6.2 2.3zm44.2-1.7c-2.9.7-4.9 2.6-4.6 4.9.3 2 2.9 3.3 5.9 2.6 2.9-.7 4.9-2.6 4.6-4.6-.3-1.9-3-3.2-5.9-2.9zM244.8 8C106.1 8 0 113.3 0 252c0 110.9 69.8 205.8 169.5 239.2 12.8 2.3 17.3-5.6 17.3-12.1 0-6.2-.3-40.4-.3-61.4 0 0-70 15-84.7-29.8 0 0-11.4-29.1-27.8-36.6 0 0-22.9-15.7 1.6-15.4 0 0 24.9 2 38.6 25.8 21.9 38.6 58.6 27.5 72.9 20.9 2.3-16 8.8-27.1 16-33.7-55.9-6.2-112.3-14.3-112.3-110.5 0-27.5 7.6-41.3 23.6-58.9-2.6-6.5-11.1-33.3 2.6-67.9 20.9-6.5 69 27 69 27 20-5.6 41.5-8.5 62.8-8.5s42.8 2.9 62.8 8.5c0 0 48.1-33.6 69-27 13.7 34.7 5.2 61.4 2.6 67.9 16 17.7 25.8 31.5 25.8 58.9 0 96.5-58.9 104.2-114.8 110.5 9.2 7.9 17 22.9 17 46.4 0 33.7-.3 75.4-.3 83.6 0 6.5 4.6 14.4 17.3 12.1C428.2 457.8 496 362.9 496 252 496 113.3 383.5 8 244.8 8zM97.2 352.9c-1.3 1-1 3.3.7 5.2 1.6 1.6 3.9 2.3 5.2 1 1.3-1 1-3.3-.7-5.2-1.6-1.6-3.9-2.3-5.2-1zm-10.8-8.1c-.7 1.3.3 2.9 2.3 3.9 1.6 1 3.6.7 4.3-.7.7-1.3-.3-2.9-2.3-3.9-2-.6-3.6-.3-4.3.7zm32.4 35.6c-1.6 1.3-1 4.3 1.3 6.2 2.3 2.3 5.2 2.6 6.5 1 1.3-1.3.7-4.3-1.3-6.2-2.2-2.3-5.2-2.6-6.5-1zm-11.4-14.7c-1.6 1-1.6 3.6 0 5.9 1.6 2.3 4.3 3.3 5.6 2.3 1.6-1.3 1.6-3.9 0-6.2-1.4-2.3-4-3.3-5.6-2z"></path></svg><!-- <i class="fab fa-github fa-fw"></i> --> </a><a class="share_twitter" data-share="twitter" href="https://twitter.com/segment_fault" target="_blank"><svg class="svg-inline--fa fa-twitter fa-w-16 fa-fw" aria-hidden="true" focusable="false" data-prefix="fab" data-icon="twitter" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512" data-fa-i2svg=""><path fill="currentColor" d="M459.37 151.716c.325 4.548.325 9.097.325 13.645 0 138.72-105.583 298.558-298.558 298.558-59.452 0-114.68-17.219-161.137-47.106 8.447.974 16.568 1.299 25.34 1.299 49.055 0 94.213-16.568 130.274-44.832-46.132-.975-84.792-31.188-98.112-72.772 6.498.974 12.995 1.624 19.818 1.624 9.421 0 18.843-1.3 27.614-3.573-48.081-9.747-84.143-51.98-84.143-102.985v-1.299c13.969 7.797 30.214 12.67 47.431 13.319-28.264-18.843-46.781-51.005-46.781-87.391 0-19.492 5.197-37.36 14.294-52.954 51.655 63.675 129.3 105.258 216.365 109.807-1.624-7.797-2.599-15.918-2.599-24.04 0-57.828 46.782-104.934 104.934-104.934 30.213 0 57.502 12.67 76.67 33.137 23.715-4.548 46.456-13.32 66.599-25.34-7.798 24.366-24.366 44.833-46.132 57.827 21.117-2.273 41.584-8.122 60.426-16.243-14.292 20.791-32.161 39.308-52.628 54.253z"></path></svg><!-- <i class="fab fa-twitter fa-fw"></i> --> </a></div>
            </div>
        </div>
    </div>
</footer>
    </div>
</template>

<script lang="ts" src="./home.component.ts">
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
    margin:0 0 0 10%;
    height: 60%;
    width: 90%;
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

.display-5{
    font-size:20px;
    margin:-75px 0 0 0;
        color: #000;

}

.display-6{
    font-size:20px;
    margin:-75px 0 0 5%;
}

.display-9{
    font-weight:normal;
}

#link{
    color: #000;
}
#link1{
        font-size:20px;
    margin:-75px 0 0 0;
        color: #000;
        }
#login{
    margin:0 0 0 4%;
}
</style>
