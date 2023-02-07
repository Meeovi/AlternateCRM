<template>
  <v-app :theme="theme">
    <v-app-bar id="topnav" density="compact">
      <template v-slot:prepend>
        <v-btn variant="flat" @click="drawer = !drawer">
          <v-icon start icon="fas fa-bars"></v-icon> Menu
        </v-btn>
      </template>
      <v-app-bar-title><a class="logobrand" href="/">
          <v-icon start icon="fas fa-users"></v-icon>AlternateCRM
        </a></v-app-bar-title>
      <v-spacer></v-spacer>

      <v-text-field density="compact" variant="solo" label="Search..." append-inner-icon="fas fa-search" single-line
        hide-details @click:append-inner="onClick"></v-text-field>
      <v-spacer></v-spacer>

      <div class="d-flex justify-space-around align-center flex-column flex-sm-row fill-height">
        <v-col>
          <v-btn :prepend-icon="theme === 'dark' ? 'fas fa-sun' : 'fas fa-moon'" @click="onClick"></v-btn>
        </v-col>
        <v-col>
          <v-btn variant="flat" href="/admin/user/">
            <v-icon start icon="fas fa-user-circle"></v-icon>
          </v-btn>
        </v-col>
        <v-col>
          <v-btn variant="flat">
            <v-icon start icon="fas fa-bell"></v-icon>
          </v-btn>
        </v-col>
      </div>
    </v-app-bar>

    <v-main>
      <v-card>
        <v-layout>
          <v-navigation-drawer expand-on-hover v-model="drawer" :rail="rail" @click="rail = false">
            <v-list-item prepend-icon="fas fa-user" title="Profile Name">
              <template v-slot:append>
                <v-btn variant="text" icon="fas fa-chevron-left" @click.stop="rail = !rail"></v-btn>
              </template>
            </v-list-item>

            <v-divider></v-divider>

            <v-list density="compact" nav>
              <v-list-item prepend-icon="fas fa-home" title="Home" value="home" href="/"></v-list-item>
              <v-list-item prepend-icon="fas fa-file-invoice" title="Accounts" value="Accounts" href="/Admin/Accounts"></v-list-item>
              <v-list-item prepend-icon="fas fa-users" title="Contacts" value="Contacts" href="/Admin/Contacts/"></v-list-item>
              <v-list-item prepend-icon="fas fa-user-doctor" title="Opportunities" value="Opportunities" href="/Admin/Opportunities"></v-list-item>
              <v-list-item prepend-icon="fas fa-person-walking-arrow-right" title="Leads" value="Leads" href="/Admin/Leads"></v-list-item>
              <v-list-item prepend-icon="fas fa-calendar-days" title="Calendar" value="Calendar" href="/Admin/Calendar"></v-list-item>
              <v-list-item prepend-icon="fas fa-hand-holding-dollar" title="Quotes" value="Quotes" href="/Admin/Quotes"></v-list-item>
              <v-list-item prepend-icon="fas fa-folder-open" title="Documents" value="Documents" href="/Admin/Documents"></v-list-item>
              <v-list-item prepend-icon="fas fa-envelope" title="Emails" value="Emails" href="/Admin/Emails"></v-list-item>
              <v-list-item prepend-icon="fas fa-bullhorn" title="Campaigns" value="Campaigns" href="/Admin/Campaigns"></v-list-item>
              <v-list-item prepend-icon="fas fa-icons" title="Media Manager" value="media manager" href="/Admin/Media/"></v-list-item>
              <v-list-item prepend-icon="fas fa-file-contract" title="Contracts" value="Contracts" href="/Admin/Contracts"></v-list-item>
              <v-list-item prepend-icon="fas fa-cubes" title="Integrations" value="integrations" href="/Admin/Integrations/"></v-list-item>
              <v-list-item prepend-icon="fas fa-gear" title="Settings" value="settings" href="/Admin/Settings/general-settings"></v-list-item>
            </v-list>            
          </v-navigation-drawer>
          <v-main id="sidebarNav"></v-main>
          <main id="mainSection">
            <slot />
          </main>
        </v-layout>
      </v-card>

    </v-main>
  </v-app>
</template>

<script>
  export default {
    data() {
      return {
        drawer: null,
        location: 'bottom',
        rail: true,
        loaded: false,
        loading: false,
      }
    },

    methods: {
      onClick() {
        this.loading = true

        setTimeout(() => {
          this.loading = false
          this.loaded = true
        }, 2000)
      },
    },
  }
</script>

<script setup>
  import {
    ref
  } from 'vue'

  const theme = ref('dark')

  function onClick() {
    theme.value = theme.value === 'light' ? 'dark' : 'light'
  };
</script>