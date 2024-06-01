<template>
  <aside :class="{ active: is_expanded }">
    <div class="logo">
      <img src="../assets/logo.png" alt="" />
    </div>
    <div class="menu-toggle-wrap">
      <button class="btn menu-toggle" @click="toggleMenu">
        <span class="material-icons">arrow_forward_ios</span>
      </button>
    </div>
    <!-- Menu container -->
    <div class="menu-container">
      <routerLink
        class="button"
        v-for="destination in destinations"
        :key="destination.id"
        :to="{
          name: 'destination.show',
          params: { id: destination.id, slug: destination.slug },
        }"
      >
        <span class="material-icons">home</span>
        <span class="text">{{ destination.name }}</span>
      </routerLink>
    </div>
    <!-- End Menu -->
  </aside>
</template>
<script>
import sourceData from "@/data.json";
export default {
  data() {
    return {
      is_expanded: false,
      destinations: sourceData.destinations,
    };
  },
  methods: {
    toggleMenu() {
      this.is_expanded = !this.is_expanded;
      console.log(this.is_expanded);
    },
  },
};
</script>
<style lang="scss" scoped>
aside {
  display: flex;
  flex-direction: column;
  width: calc(2rem + 32px);
  overflow: hidden;
  min-height: calc(100vh - 72px);
  padding: 1rem;
  background-color: rgb(171, 167, 167);
  transition: 0.2s ease-out;

  .logo {
    margin-bottom: 1rem;
    img {
      width: 2rem;
    }
  }

  .menu-toggle-wrap {
    display: flex;
    justify-content: flex-end;
    position: relative;
    top: 0;
    transition: 0.2s ease-out;
    margin-bottom: 1rem;
    .menu-toggle {
      transition: 0.2s ease-out;
      .material-icons {
        transition: 0.2s ease-out;
      }
      &:hover {
        .material-icons {
          color: rgb(17, 214, 122);
          transform: translateX(0.3rem);
        }
      }
    }
  }

  .menu-container {
    display: flex;
    flex-direction: column;
    .button {
      display: flex;
      align-items: center;
      justify-content: flex-start;
      margin-bottom: 1rem;
      color: rgb(18, 48, 69);
      .material-icons {
        font-size: 2rem;
        transition: 0.2s ease-out;
      }
      .text {
        opacity: 0;
        transition: 0.2s ease-out;
      }
      &:hover,
      &.router-link-exact-active {
        background-color: rgb(44 62 80 / 43%);
        .material-icons,
        .text {
          color: rgb(17, 214, 122);
        }
      }
    }
  }

  &.active {
    width: 300px;

    .menu-toggle-wrap {
      top: -3rem;
      .menu-toggle {
        transform: rotate(-180deg);
      }
    }

    .menu-container {
      .button {
        .material-icons {
          margin-right: 1rem;
        }
        .text {
          opacity: 1;
        }
      }
    }
  }
}

@media (max-width: 768px) {
  aside {
    position: fixed;
    z-index: 99;
  }
}
</style>
