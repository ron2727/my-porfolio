<template>
    <div  ref="pageScroll" class="page-scroll group fixed bottom-0 right-0">
        <Transition name="slide">
            <div class="flex flex-col items-center mr-3 mb-7" v-if="toggelRocket">
                <a id="to-top" href="#intro">
                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor"
                        class="size-10 text-sky-600 -rotate-45">
                        <path fill-rule="evenodd"
                            d="M9.315 7.584C12.195 3.883 16.695 1.5 21.75 1.5a.75.75 0 0 1 .75.75c0 5.056-2.383 9.555-6.084 12.436A6.75 6.75 0 0 1 9.75 22.5a.75.75 0 0 1-.75-.75v-4.131A15.838 15.838 0 0 1 6.382 15H2.25a.75.75 0 0 1-.75-.75 6.75 6.75 0 0 1 7.815-6.666ZM15 6.75a2.25 2.25 0 1 0 0 4.5 2.25 2.25 0 0 0 0-4.5Z"
                            clip-rule="evenodd" />
                        <path
                            d="M5.26 17.242a.75.75 0 1 0-.897-1.203 5.243 5.243 0 0 0-2.05 5.022.75.75 0 0 0 .625.627 5.243 5.243 0 0 0 5.022-2.051.75.75 0 1 0-1.202-.897 3.744 3.744 0 0 1-3.008 1.51c0-1.23.592-2.323 1.51-3.008Z" />
                    </svg> 
                </a>
                <small class=" text-sky-600 opacity-0 transition-opacity duration-700 group-hover:opacity-100">
                    Go to the top
                </small>
            </div>
        </Transition>
    </div>
</template>

<script setup>

import { onMounted, ref } from 'vue'

const pageScroll = ref(null);
const toggelRocket = ref(false);

onMounted(() => {
    const projectSection = document.getElementById('projects');
    window.addEventListener('scroll', () => {
        const scrollTop = window.scrollY;
        if (scrollTop > projectSection.offsetTop) {
            toggelRocket.value = true;
        } else {
            toggelRocket.value = false;
        }
    })
}) 
</script>

<style> 
/* Transition animations */
.slide-enter-active,
.slide-leave-active {
  transition: transform 0.5s ease-out, opacity 0.5s ease-out;
}

.slide-enter-from {
  transform: translateY(100%);
  opacity: 0;
}

.slide-enter-to {
  transform: translateY(0);
  opacity: 1;
}

.slide-leave-from {
  transform: translateY(0);
  opacity: 1;
}

.slide-leave-to {
  transform: translateY(100%);
  opacity: 0;
}
</style>