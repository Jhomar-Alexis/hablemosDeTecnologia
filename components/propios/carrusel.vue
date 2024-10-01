<template>
    <UCarousel ref="carouselRef" v-slot="{ item }" :items="items" :ui="{ item: 'basis-full' }"
        class="overflow-hidden relative bg-gray-200" indicators>
        <div class="relative h-[100vh] w-full flex justify-center items-center">
            <img :src="item" class="h-4/5 w-4/5 mx-auto rounded-lg border-8 border-cyan-700" draggable="false">
            <div class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 
          text-gray-800 text-lg flex flex-col items-center justify-center">
                <div class="text-center">
                    <span class="lg:text-[90px] md:text-[60px] text-[36px]" style="font-weight: 900;">LA</span>
                </div>
                <div class="text-center mt-4">
                    <span class="lg:text-[90px] md:text-[60px] text-[36px]" style="font-weight: 900;">TECNOLÓGIA</span>
                </div>
            </div>
        </div>
    </UCarousel>
</template>
<script setup>
const items = [
    '/images/1.jpeg',
    '/images/2.jpeg',
    '/images/3.jpeg',
    '/images/4.jpeg'
]

const carouselRef = ref()

onMounted(() => {
    setInterval(() => {
        if (!carouselRef.value) return

        if (carouselRef.value.page === carouselRef.value.pages) {
            return carouselRef.value.select(0)
        }

        carouselRef.value.next()
    }, 3000)
})
</script>