<template>
    <main>
        <h1>Homepage</h1>
        <nav>
            <ul>
                <li>
                    <nuxt-link to="/">Homepage</nuxt-link>
                </li>
                <li>
                    <nuxt-link to="/about">About</nuxt-link>
                </li>
                <li>
                    <nuxt-link to="/contact">Contact</nuxt-link>
                </li>
            </ul>
        </nav>
        <h2>Products</h2>
        <ul class="product-list">
            <li>
                <nuxt-link to="/products/1">Product #1</nuxt-link>
            </li>
            <li>
                <nuxt-link to="/products/2">Product #2</nuxt-link>
            </li>
            <li>
                <nuxt-link to="/products/3">Product #3</nuxt-link>
            </li>
        </ul>
        <div id="container">
            <svg id="motion-path" viewBox="0 0 800 400" xmlns="http://www.w3.org/2000/svg">
                <path id="path"
                      d="M198,15 c-5,76 33,47 36,140 c-1,56 -40,60 -39,112 c-5,65 32,68 38,124 c-1,54 -42,36 -43,102"
                      fill="none" stroke-dasharray="0 0" stroke-linecap="butt"
                      stroke-width="1"
                ></path>
            </svg>
            <div id="target">
                <img alt="ant" class="ant" src="/images/ant-spritesheet.png"/>
            </div>
        </div>
    </main>
</template>

<script lang="ts" setup>
import {gsap} from "gsap";
import {MotionPathPlugin} from "gsap/MotionPathPlugin";
import {ScrollTrigger} from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger, MotionPathPlugin);

onMounted(() => {
    const animatedDiv = document.querySelector("#target");

    let sprite = document.querySelector('.ant'),
        sw = sprite!.clientWidth,
        frameCount = 3;

    gsap.set('#target', {width: sw! / (frameCount + 1)});

    gsap.timeline({
        scrollTrigger: {
            trigger: "#motion-path",
            start: "top center",
            end: "bottom center",
            pin: true,
            scrub: true,
            onRefresh: () => {
                sw = sprite!.clientWidth;
                gsap.set('#target', {width: sw / (frameCount + 1)});
                //self.scroll(self.scrollX, self.scrollY);
            },
            invalidateOnRefresh: true
        }
    })
        .to(".ant", {
            x: () => {
                return -sprite!.clientWidth * (1 - 1 / (frameCount + 1));
            },
            repeat: 10,
            ease: "steps(" + frameCount + ")",
        });

    gsap.to(animatedDiv, {
        scrollTrigger: {
            trigger: "#motion-path",
            start: "top center",
            end: "bottom center",
            scrub: true,
        },
        ease: "power1.inOut",
        immediateRender: true,
        motionPath: {
            path: "#path",
            align: "#path",
            alignOrigin: [0.5, 0.5],
            autoRotate: 180,
        },
    });
})

</script>

<style>
#container {
    width: 100%;
    height: 1000px;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
}

#target {
    width: calc(305px / 4);
    height: 80px;
    overflow: clip;
}

.product-list {
    margin-bottom: 100px;
}

#path {
    color: transparent;
}

.ant {
    position: relative;
    height: 100%;
}

</style>