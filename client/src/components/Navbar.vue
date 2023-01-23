<script>
export default {
    emits : ['changePage'],
    methods : {
        changePage(page){
            this.$emit('changePage', page)
        }
    }
}
</script>

<template>
    <div class="btm-nav">
        <button class="bg-pink-200 text-pink-600" @click.prevent="changePage('home')">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1v-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 001 1m-6 0h6" /></svg>
            <span class="btm-nav-label">Home</span>
        </button>
        <button class="active bg-neutral text-neutral-content" @click.prevent="changePage('list')">
            <i class="fa-solid fa-list"></i>
            <span class="btm-nav-label">List</span>
        </button>
        <button class="bg-teal-200 text-teal-600" @click.prevent="changePage('user')">
            <i  class="fa-regular fa-user"></i>
            <span class="btm-nav-label">Account</span>
        </button>
    </div>
</template>