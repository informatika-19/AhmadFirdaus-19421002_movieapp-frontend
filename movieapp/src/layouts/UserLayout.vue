<template>
  <q-layout view="lHh LpR fFf">
     <q-toolbar unelevated style="height: 60px" class="bg-green-3 text-blue-gray-14">
      <div class="text-h5 q-ml-lg">Movie App</div>
      <q-space />
      <div v-if="$q.screen.md || $q.screen.lg || $q.screen.xl">
      <q-btn :to="{ name: 'homeUser' }" size="medium" flat >Home</q-btn>
      <q-btn :to="{ name: 'myOrder' }" size="medium" flat >peasanan</q-btn>
      <q-btn size="medium" flat >tentang</q-btn>
      <q-btn size="medium" @click="logout()" flat >logout</q-btn>
      </div>
      <q-btn size="medium" round flat icon="shopping_cart" />
      <q-btn flat round @click="leftDrawerOpen = !leftDrawerOpen" v-if="$q.screen.xs ||$q.screen.sm " icon="menu"/>
    </q-toolbar>
      <q-drawer
        v-model="leftDrawerOpen"
        :width="200"
        :breakpoint="500"
      >
        <q-scroll-area class="fit">
          <q-list padding class="menu-list">
            <q-item clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="home" />
              </q-item-section>
              <q-item-section>
                Home
              </q-item-section>
            </q-item>
          </q-list>
        </q-scroll-area>
      </q-drawer>

    <q-page-container class="bg-gray-2">
      <router-view />
    </q-page-container>
  </q-layout>
</template>
<script>
export default {
  name: 'userLayout',
  data () {
    return {
      leftDrawerOpen: false
    }
  },
  methods: {
    logout () {
      this.$q.localStorage.remove()
      this.$router.push({ name: 'loginPage' })
    }
  }
}
</script>
