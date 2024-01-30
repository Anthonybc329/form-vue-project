
<template>
    <div>
        <nav>
            <RouterLink to="data.path">{{ data.name }}</RouterLink>
        </nav>
    </div>
</template>
<script lang="ts" setup>
import type IMenuItem from '@/interface/IMenuItem';

const data = defineProps<IMenuItem>();
</script>


