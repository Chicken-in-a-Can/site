<script setup>
    import { ref, computed } from "vue";

    const mouseX = ref(0);
    const mouseY = ref(0);
    const hovering = ref(false);
    const glowColor = ref('');

    function updateMousePosition(event) {
        const rect = event.currentTarget.getBoundingClientRect();
        mouseX.value = event.clientX - rect.left;
        mouseY.value = event.clientY - rect.top;
    }

    const glowStyle = computed(() => ({
        '--x': `${mouseX.value}px`,
        '--y': `${mouseY.value}px`,
    }));

    const glowContainerClass = computed(() => {
        if (!hovering.value) {
            return '';
        }

        return `bg-[radial-gradient(128px_at_var(--x)_var(--y),rgba(187,154,247,0.15),transparent_80%)]`;
    });

</script>

<template>
    <div 
      @mouseenter="hovering = true"
      @mouseleave="hovering = false"
      @mousemove="updateMousePosition"
      :class="glowContainerClass"
      :style="glowStyle"
      class="overflow-hidden transition-all duration-300 bg-(color:--bg) border-2 rounded-xl inset-shadow-sm/50 inset-shadow-(color:--blue) cursor-none">
        <slot></slot>
    </div>
</template>
