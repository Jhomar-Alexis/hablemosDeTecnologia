<template>
    <!-- barra de navegacion -->
    <div
        class="flex justify-between sm:justify-between z-50 items-center px-2 lg:px-4 h-14 w-[80vw] shadow-[0_0_20px_0] bg-gray-200 rounded-3xl text-black">
        <!-- logo -->
        <div class="flex items-center">
            <img src="~/public/images/portada.jpeg" alt="logo" class="w-8 h-8 sm:w-10 sm:h-10 rounded-full">
            <h1 class="text-xl font-[900] ml-2">TIC</h1>
        </div>
        <div class="flex items-center gap-1">
            <!-- regresar -->
            <Button size="icon" ref="btn" variant="outline" @click="router.push('/')"
                class="rounded-full w-10 h-10 p-1">
                <Icon name="i-ph-arrow-left" class="w-6 h-6" />
            </Button>

            <!-- boton de hamburguesa -->
            <div class="sm:hidden">
                <Button size="icon" ref="btn" variant="outline" class="rounded-full w-10 h-10 p-1"
                    @click="toggleSidebar">
                    <Icon name="i-carbon-menu" class="w-9 h-9" />
                </Button>
            </div>
        </div>
    </div>

    <!-- barra lateral -->
    <div ref="sidebar"
        class="hidden sm:flex lg:items-center sm:-mt-[3.2rem] pt-2 sm:pt-0 sm:pl-6 md:pl-0 justify-center">
        <div class="grid sm:flex gap-4 lg:gap-8 border sm:border-none font-bold bg-gray-200
            sm:p-0 shadow-[0_0_20px_0] sm:shadow-none p-20 rounded-3xl text-center text-black"
            style="cursor: pointer;">
            <a v-for="link in links" :key="link" @click.prevent="scrollTo(link.target)">
                <Icon :name="link.icon" class=" text-2xl sm:text-xl" />
                <br /> {{ link.name }}
            </a>
        </div>
    </div>
</template>

<script setup>
import { useRouter } from 'vue-router';
const router = useRouter();

const links = [
    {
        icon: 'i-ph-house',
        name: 'Inicio',
        target: 'inicio'
    },
    {
        icon: 'i-ph-list-dashes',
        name: 'Usos',
        target: 'usos'
    },
    {
        icon: 'i-mdi-alert',
        name: 'Riesgos',
        target: 'riesgos'
    },
    {
        icon: 'i-mdi-shield',
        name: 'Prevención',
        target: 'prevencion'
    },
    {
        icon: 'i-mdi-shield-half-full',
        name: 'Prevención/Niños',
        target: 'prevencionniños'
    },
]

const btn = ref(null)
const sidebar = ref(null)

const toggleSidebar = () => {
    // sidebar.value?.classList?.toggle('animate-fade-left');
    sidebar.value?.classList?.toggle('hidden');
    btn.value?.classList?.toggle('hidden');
}

const scrollTo = (target) => {
    const element = document.getElementById(target);
    element.scrollIntoView({ behavior: 'smooth' });
}
</script>