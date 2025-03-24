<template>
    <div class="slider">
        <div class="item" v-for="(slide, index) in slides" :key="index" v-show="currentIndex === index">
            <img :src="slide.image" :alt="slide.title" />

            <div class="content">
                <div class="title">{{ slide.title }}</div>
                <div class="type">{{ slide.type }}</div>
                <div class="description">{{ slide.description }}</div>
                <div class="button">
                    <button @click="showMore(slide)">DAHA FAZLA GÖR</button>
                </div>
            </div>
        </div>

        <div class="controls">
            <button @click="prevSlide">&lt;</button>
            <button @click="nextSlide">&gt;</button>
        </div>
    </div>
</template>

<script setup>
import { ref } from "vue";

// Kaydırıcı içeriği
const slides = ref([
    {
        title: "SİHİRLİ KAYDIRICI",
        type: "BİTKİ",
        description:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Deleniti temporibus quis eum consequuntur voluptate quae doloribus distinctio.",
        image: new URL("@/assets/image/img4.jpg", import.meta.url).href
    },
    {
        title: "SİHİRLİ KAYDIRICI",
        type: "DOĞA",
        description:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Deleniti temporibus quis eum consequuntur voluptate quae doloribus distinctio.",
        image: new URL("@/assets/image/img3.jpg", import.meta.url).href
    }
]);

const currentIndex = ref(0);

// Önceki slayta geçiş
const prevSlide = () => {
    currentIndex.value = (currentIndex.value - 1 + slides.value.length) % slides.value.length;
};

// Sonraki slayta geçiş
const nextSlide = () => {
    currentIndex.value = (currentIndex.value + 1) % slides.value.length;
};

// Daha fazla gör butonu
const showMore = (slide) => {
    alert(`${slide.title} hakkında daha fazla bilgi yakında eklenecek!`);
};
</script>

<style scoped>
.slider {
    position: relative;
    width: 100%;
    max-width: 800px;
    margin: auto;
    overflow: hidden;
}

.item {
    position: relative;
    text-align: center;
}

.item img {
    width: 100%;
    border-radius: 10px;
}

.content {
    position: absolute;
    bottom: 20px;
    left: 20px;
    background: rgba(0, 0, 0, 0.6);
    color: white;
    padding: 15px;
    border-radius: 5px;
}

.title {
    font-size: 20px;
    font-weight: bold;
}

.type {
    font-size: 16px;
    color: #14ff72;
}

.description {
    font-size: 14px;
    margin-top: 10px;
}

.button button {
    margin-top: 10px;
    padding: 8px 15px;
    background: #14ff72;
    border: none;
    color: black;
    font-weight: bold;
    cursor: pointer;
    border-radius: 5px;
}

.controls {
    display: flex;
    justify-content: space-between;
    position: absolute;
    top: 50%;
    width: 100%;
    transform: translateY(-50%);
}

.controls button {
    background: rgba(0, 0, 0, 0.6);
    color: white;
    border: none;
    padding: 10px 15px;
    cursor: pointer;
    font-size: 18px;
}
</style>
