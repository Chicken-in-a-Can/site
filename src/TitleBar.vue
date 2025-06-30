<script setup>
    import { ref } from "vue";
    import { RouterLink, useRoute } from 'vue-router';
    import logo from "./assets/logo.svg";
    import { computed } from "vue";
    import ScreenDiv from "./ScreenDiv.vue";

    const route = useRoute();

    const current_path = computed(() => route.path);

    const page_links = ref(["/", "/portfolio", "/about"]);
    const page_titles = ref(["Home", "Portfolio", "About"]);
</script>

<template>
    <div class="main-font">
        <ScreenDiv class="p-8 h-24 w-full">
            <ul class="font-large flex flex-col p-4 md:p-0 mt-4 border border-gray-100 rounded-lg md:flex-row md:space-x-8 rtl:space-x-reverse md:mt-0 md:border-0">
                <li v-for="(title, index) in page_titles" :key="title">
                    <router-link :to="page_links[index]" class="">
                        <div class="overflow-hidden transition-all duration-300 bg-(color:--blue)/50 border-2 border-(color:--blue) rounded-lg inset-shadow-sm/50 inset-shadow-(color:--blue) hover:bg-(color:--magenta2)/50 hover:border-(color:--magenta2) hover:inset-shadow-(color:--magenta2)">
                            <span v-if="current_path === page_links[index]" class="m-8 text-(color:--bg)">
                                {{ title }}
                            </span>
                            <span v-else class="m-8 text-(color:--bg)">
                                {{ title }}
                            </span>
                        </div>
                    </router-link>
                </li>
            </ul>
        </ScreenDiv>
    </div>
</template>
