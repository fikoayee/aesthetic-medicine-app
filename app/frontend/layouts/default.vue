<template>
  <v-app :theme="colorMode.preference">
    <v-app-bar v-if="isMobile">
      <v-btn @click="drawer = !drawer">toggle menu</v-btn>
      <color-switch v-if="isMobile"/>
    </v-app-bar>
    <v-navigation-drawer v-model="drawer"  expand-on-hover :rail="!isMobile" :permanent="!isMobile">
      <v-list>
        <v-list-item
          prepend-avatar="https://randomuser.me/api/portraits/women/85.jpg"
          subtitle="sandra_a88@gmailcom"
          title="Sandra Adams"
        ></v-list-item>
        <v-divider></v-divider>
        <v-list-item
          prepend-icon="mdi-folder"
          title="Treatments"
          value="treatments"
        ></v-list-item>
        <color-switch v-if="!isMobile"/>
      </v-list>
    </v-navigation-drawer>
    <v-main>
      <slot />
    </v-main>
  </v-app>
</template>
<script setup langs="ts">
const colorMode = useColorMode();
const viewport = useViewport();

const drawer = ref(true);

const isMobile = computed(()=>{
    return viewport.isLessThan('tablet')
})

</script>
