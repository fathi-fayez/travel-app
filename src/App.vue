<!-- eslint-disable -->
<template>
  <div>
    <TheNavigation />
    <div class="main">
      <side-bar></side-bar>
      <router-view class="router-view" v-slot="{ Component }">
        <transition name="fade" mode="out-in">
          <component :is="Component" :key="$route.path"></component>
        </transition>
      </router-view>
    </div>
  </div>
</template>
<!-- eslint-disable -->
<script>
import TheNavigation from "@/components/TheNavigation.vue";
import SideBar from "./components/SideBar.vue";
export default {
  components: { TheNavigation, SideBar },
};
</script>
<style lang="css">
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}
.main {
  display: flex;
}
.main .router-view {
  flex: 1 1 0;
  padding: 2rem;
}
@media (max-width: 768px) {
  .main .router-view {
    padding-left: 6rem;
  }
}
</style>
