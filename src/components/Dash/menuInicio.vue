<template>
  <q-header elevated class="bg-white text-grey-8" height-hint="64">
    <q-toolbar class="GNL__toolbar">
      <q-btn flat @click="drawer = !drawer" round dense icon="menu" />
      <q-toolbar-title
        v-if="$q.screen.gt.xs"
        shrink
        class="row items-center no-wrap"
      >
        <span class="q-ml-sm">Comtrato</span>
      </q-toolbar-title>

      <q-space />

      <q-space />

      <div class="q-gutter-sm row items-center no-wrap">
        <q-btn
          v-if="$q.screen.gt.sm"
          round
          dense
          flat
          color="text-grey-7"
          icon="apps"
        >
          <q-tooltip>Menu</q-tooltip>
        </q-btn>
        <q-btn round dense flat color="grey-8" icon="notifications">
          <q-badge color="red" text-color="white" floating> 5 </q-badge>
          <q-tooltip>Notificações</q-tooltip>
        </q-btn>
        <q-btn round flat>
          <q-avatar size="26px">
            <img src="https://cdn.quasar.dev/img/boy-avatar.png" />
          </q-avatar>
          <q-tooltip>Minha Conta</q-tooltip>
        </q-btn>
      </div>
    </q-toolbar>
  </q-header>
  <q-drawer
    v-model="drawer"
    show-if-above
    :width="200"
    :breakpoint="500"
    bordered
    class="bg-grey-3"
  >
    <q-scroll-area class="fit">
      <q-list>
        <template v-for="(menuItem, index) in menuList" :key="index">
          <q-item clickable :active="menuItem.label === 'Outbox'" v-ripple>
            <q-item-section avatar>
              <q-icon :name="menuItem.icon" />
            </q-item-section>
            <q-item-section>
              {{ menuItem.label }}
            </q-item-section>
          </q-item>
          <q-separator :key="'sep' + index" v-if="menuItem.separator" />
        </template>
      </q-list>
    </q-scroll-area>
  </q-drawer>
</template>

<script>
import { ref } from "vue";

const menuList = [
  {
    icon: "add",
    label: "Novo Comtrato",
    separator: true,
  },
  {
    icon: "article",
    label: "Meus Contratos",
    separator: false,
  },
  {
    icon: "description",
    label: "Relatórios",
    separator: false,
  },
  {
    icon: "error",
    label: "Spam",
    separator: true,
  },
  {
    icon: "settings",
    label: "Configurações",
    separator: false,
  },
  {
    icon: "feedback",
    label: "Feedback",
    separator: false,
  },
  {
    icon: "help",
    iconColor: "primary",
    label: "Ajuda",
    separator: false,
  },
];
export default {
  name: "menuInicio",
  setup() {
    return {
      drawer: ref(false),
      menuList,
    };
  },
};
</script>

<style lang="sass">
.GNL
  &__toolbar
    height: 64px
  &__toolbar-input
    width: 55%
  &__drawer-item
    line-height: 24px
    border-radius: 0 24px 24px 0
    margin-right: 12px
    .q-item__section--avatar
      .q-icon
        color: #5f6368
    .q-item__label
      color: #3c4043
      letter-spacing: .01785714em
      font-size: .875rem
      font-weight: 500
      line-height: 1.25rem
  &__drawer-footer-link
    color: inherit
    text-decoration: none
    font-weight: 500
    font-size: .75rem
    &:hover
      color: #000
</style>
