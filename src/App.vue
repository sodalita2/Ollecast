<script setup>
import { RouterLink, RouterView } from 'vue-router';
import axios from 'axios';
import $ from 'jquery';
import HeaderNav from './components/HeaderNav.vue';

</script>

<template>
    <HeaderNav />
    <RouterView />
</template>
