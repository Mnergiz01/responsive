<template>
    <div>
        <header>
            <nav>
                <a 
                    v-for="(link, index) in links" 
                    :key="index" 
                    :href="link.href" 
                    :class="{ active: activeLink === link.name }"
                    @click.prevent="setActiveLink(link.name)"
                >
                    {{ link.name }}
                </a>
            </nav>
        </header>
    </div>
</template>

<script setup>
import { ref } from "vue";

// Menü linklerini tanımla
const links = ref([
    { name: "Ana Sayfa", href: "#" },
    { name: "Hakkında", href: "#" },
    { name: "Portföy", href: "#" },
    { name: "Hizmetler", href: "#" },
    { name: "İletişim", href: "#" }
]);

// Aktif bağlantıyı takip eden reaktif değişken
const activeLink = ref("Ana Sayfa");

// Aktif bağlantıyı değiştir
const setActiveLink = (name) => {
    activeLink.value = name;
};
</script>

<style scoped>
header {
    width: 100%;
    background: #222;
    padding: 15px 0;
    display: flex;
    justify-content: center;
}

nav a {
    color: white;
    text-decoration: none;
    margin: 0 15px;
    padding: 10px;
    transition: 0.3s;
    font-size: 16px;
}

nav a.active, nav a:hover {
    background: #14ff72cb;
    border-radius: 5px;
}
</style>
