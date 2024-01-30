<template>
    <div>
        <MenuItem v-for="routes in routeViews" :name="routes.name" :path="routes.path"></MenuItem>
    </div>
</template>
<script lang="ts" setup>
import type IMenuItem from '@/interface/IMenuItem';
import MenuItem from './MenuItem.vue';
import router from '@/router';


const routeViews = router.options.routes.filter(route => {

    return {name: route.name, path: route.path};
}) as IMenuItem[];
</script>