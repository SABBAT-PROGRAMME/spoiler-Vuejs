<!-- tamplate -->
<template>
  <Transition name="fade">
    <slot></slot>
  </Transition>
</template>

<!-- style -->
<style>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}
fade-enter-from,
fade-leave-to {
  opacity: 0;
}
</style>
