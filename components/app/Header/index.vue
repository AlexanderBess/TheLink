<template>
  <div class="menu">
    <nuxt-link
        v-for="(link, key) in menuLinks"
        :key="key"
        class="menu__link-block"
        :to="link.path">
      <img :src="link.icon" :alt="link.name">
      <div
          class="menu__link-text"
          :class="linkColor(link.path)">
        {{ link.name }}
      </div>
    </nuxt-link>
  </div>
</template>

<script>
import {Path} from "@/utils/enums";

export default {
  name: "headerMenu",
  data() {
    return {
      menuLinks: {
        profile: {
          name: this.$t('menu.profile'),
          icon: require('~/assets/img/ui/profile.svg'),
          path: Path.PROFILE
        },
        link: {
          name: this.$t('menu.link'),
          icon: require('~/assets/img/ui/link.svg'),
          path: Path.CONTACTS
        },
        design: {
          name: this.$t('menu.design'),
          icon: require('~/assets/img/ui/design.svg'),
          path: Path.DESIGN
        },
        share: {
          name: this.$t('menu.share'),
          icon: require('~/assets/img/ui/share.svg'),
          path: Path.SHARE
        },
        preview: {
          name: this.$t('menu.preview'),
          icon: require('~/assets/img/ui/preview.svg'),
          path: Path.PREVIEW
        }
      }
    };
  },
  methods: {
    linkColor(path) {
      if(path === this.$route.path) {
        return 'menu__link-text_active';
      }
      return '';
    }
  }
}
</script>

<style lang="scss" scoped>
.menu {
  &__link-block {
    display: flex;
    flex-direction: column;
    align-items: center;

    text-decoration: none;
  }
  &__link-text {
    font-weight: 400;
    font-size: 10px;
    line-height: 12px;

    color: $title;
    &_active {
      color: $link;
    }
  }
}
</style>
