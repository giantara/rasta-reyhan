<template>
  <div>
    <download v-if="$route.fullPath === '/download'" />
    <transition name="fade" v-else>
      <invitation-card @invite="openInvitation" v-if="invitation" />
      <home v-else />
    </transition>
  </div>
</template>

<script>
import InvitationCard from '@/components/InvitationCard.vue'
import Home from '@/views/Home.vue'
import Download from '@/views/Download.vue'

export default {
  name: 'App',
  components: {
    InvitationCard,
    Home,
    Download
  },
  data() {
    return {
      invitation: true
    }
  },
  methods: {
    openInvitation() {
      this.invitation = false
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}

html,
body {
  /* overscroll-behavior: contain; */
  width: 100%;
  height: 100%;
  margin: 0;
  overflow-x: hidden;
  overflow-y: auto;
}

body {
  width: 100%;
  height: 100%;
  background-attachment: fixed;
}

@font-face {
  font-family: 'CaviarDreamsBold';
  src: url('./assets/fonts/CaviarDreams_Bold.ttf');
}

@font-face {
  font-family: 'CaviarDreams';
  src: url('./assets/fonts/CaviarDreams.ttf');
}

@font-face {
  font-family: 'DanielBold';
  src: url('./assets/fonts/danielbd.ttf');
}

@font-face {
  font-family: 'MontHeavy';
  src: url('./assets/fonts/montHeavy.otf') format('opentype');
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
