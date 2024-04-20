<script setup lang="ts">
const colorMode = useColorMode()
const isDark = computed({
    get() {
        return colorMode.value === 'dark'
    },
    set() {
        colorMode.preference = colorMode.value === 'dark' ? 'light' : 'dark'
    }
})
// const nuxtApp = useNuxtApp()
// const { activeHeadings, updateHeadings } = useScrollspy()

const links = computed(() => [{
    label: 'Features',
    to: '#features',
    icon: 'i-heroicons-cube-transparent',
    //   active: activeHeadings.value.includes('features') && !activeHeadings.value.includes('pricing')
}, {
    label: 'Pricing',
    to: '#pricing',
    icon: 'i-heroicons-credit-card',
    //   active: activeHeadings.value.includes('pricing') && !activeHeadings.value.includes('testimonials')
}, {
    label: 'Testimonials',
    to: '#testimonials',
    icon: 'i-heroicons-academic-cap',
    //   active: activeHeadings.value.includes('testimonials')
}, {
    label: 'FAQ',
    to: '#faq',
    icon: 'i-heroicons-question-mark-circle',
    //   active: activeHeadings.value.includes('faq')
}])

// nuxtApp.hooks.hookOnce('page:finish', () => {
//   updateHeadings([
//     document.querySelector('#features'),
//     document.querySelector('#pricing'),
//     document.querySelector('#testimonials'),
//     document.querySelector('#faq')
//   ])
// })
</script>

<template>
    <UHorizontalNavigation class="fixed top-0 backdrop-blur-md bg-transparent h-32" :links="links">
        <template #logo>
            Nuxt UI Pro
            <UBadge label="Landing" variant="subtle" class="mb-0.5" />
        </template>

        <template #right>
            <UButton label="Sign in" color="white" variant="ghost" trailing-icon="i-heroicons-arrow-right-20-solid"
                class="hidden lg:flex" />
        </template>

        <template #panel>
            <!-- <UAsideLinks :links="links" /> -->

            <UDivider class="my-6" />

            <UButton label="Sign in" color="white" block class="mb-3" />
            <UButton label="Get started" block />
            <UButton>
                <ClientOnly>
                    <UButton :icon="isDark ? 'i-heroicons-moon-20-solid' : 'i-heroicons-sun-20-solid'" color="gray"
                        variant="ghost" aria-label="Theme" @click="isDark = !isDark" />
                    <template #fallback>
                        <div class="w-8 h-8" />
                    </template>
                </ClientOnly>
            </UButton>
        </template>
    </UHorizontalNavigation>
</template>
