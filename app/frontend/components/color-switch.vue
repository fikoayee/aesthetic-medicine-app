<template>
  <v-switch v-model="isDarkMode" @click="toggleColor">Toggle Theme</v-switch>
</template>
<script setup langs="ts">
const colorMode = useColorMode();
const isDarkMode = ref(false);

const toggleColor = () => {
  colorMode.preference = isDarkMode.value ? "light" : "dark";
};
const getSwitchValue = () => {
  return colorMode.preference === "dark" ? true : false;
};

onMounted(() => {
  isDarkMode.value = getSwitchValue();
});
</script>
