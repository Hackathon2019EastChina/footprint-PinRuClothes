<template>
    <div id="bg">
    <div class="home row">
        <div class="col-md-10">
            <br>
            <h1 class="display-4">&nbsp;&nbsp;&nbsp;WELCOME TO 行迹!</h1>
            <br>
            <p class="display-3">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;欢迎在这里，成为最好的你自己：be the bset of yourself</p>

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
