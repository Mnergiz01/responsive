<template>
    <div class="carousel">
        <div class="thumbnail">
            <div 
                class="item" 
                v-for="(image, index) in images" 
                :key="index" 
                :class="{ active: index === currentIndex }"
            >
                <img :src="image" alt="Thumbnail Image">
            </div>
        </div>

        <div class="nextPrevArrows">
            <button class="prev" @click="prevSlide">&lt;</button>
            <button class="next" @click="nextSlide">&gt;</button>
        </div>
    </div>
</template>

<script setup>
import { ref } from "vue";

// Resimlerin doğru yollarını almak için import kullan
import img1 from "@/assets/image/img1.jpg";
import img2 from "@/assets/image/img2.jpg";
import img3 from "@/assets/image/img3.jpg";
import img4 from "@/assets/image/img4.jpg";

// Resimleri listeye ekle
const images = ref([img1, img2, img3, img4]);

const currentIndex = ref(0);

// Önceki resme geçiş
const prevSlide = () => {
    currentIndex.value = (currentIndex.value - 1 + images.value.length) % images.value.length;
};

// Sonraki resme geçiş
const nextSlide = () => {
    currentIndex.value = (currentIndex.value + 1) % images.value.length;
};
</script>

<style scoped>
.carousel {
    position: relative;
    width: 100%;
    max-width: 600px;
    margin: auto;
    overflow: hidden;
}

.thumbnail {
    display: flex;
    justify-content: center;
    gap: 10px;
}

.item {
    opacity: 0.5;
    transition: opacity 0.3s ease-in-out;
}

.item.active {
    opacity: 1;
    border: 2px solid #14ff72;
}

.item img {
    width: 100px;
    height: auto;
    cursor: pointer;
    border-radius: 5px;
}

.nextPrevArrows {
    display: flex;
    justify-content: space-between;
    position: absolute;
    top: 50%;
    width: 100%;
    transform: translateY(-50%);
}

.nextPrevArrows button {
    background: rgba(0, 0, 0, 0.6);
    color: white;
    border: none;
    padding: 10px 15px;
    cursor: pointer;
    font-size: 18px;
}
</style>
