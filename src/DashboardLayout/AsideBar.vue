<script lang="ts" setup>
import { RouterLink, RouterView } from 'vue-router'
import AsideBarLogo from '../DashboardLayout/AsideBarLogo.vue';
import { defineStore } from 'pinia';
import { storeToRefs } from 'pinia';
import { useUserStore } from '@/stores/user';
import { onMounted, ref } from 'vue';
const { userData } = useUserStore()
const { users, UserInitialise, UserConnectData } = storeToRefs(useUserStore())

onMounted(async () => {
    await userData()
    console.log(UserConnectData)
}) 
</script>


<template>
    <aside class="asidebar">
        <div class="container">
            <div class="asidebar_content">
                <div class="asidebar_top">
                    <p>{{ UserConnectData }}</p>
                </div>
                <ul>
                    <a href="/dashboard">
                        <li>
                            <AsideBarLogo />
                            Dashboard
                        </li>
                    </a>
                    <a href="/dashboard/etudiant">
                        <li>
                            <AsideBarLogo />
                            Etudiants
                        </li>
                    </a>
                    <a href="/dashboard/matiere">
                        <li>
                            <AsideBarLogo />
                            Matières
                        </li>
                    </a>
                    <a href="#">
                        <li>
                            <AsideBarLogo />
                            Dashboard
                        </li>
                    </a>
                </ul>
                <div class="asidebar_bottom">
                    &copy;All Rigths Reserved
                </div>
            </div>
        </div>
    </aside>
</template>

<style scoped>
* {
    position: relative;
    margin: 0;
    padding: 0;
    color: white !important;
    font-size: 16px;
    font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}

a {
    text-decoration: none;
    color: black;
}

ul li {
    list-style-type: none;
}

body {
    width: 100%;
    padding: 0;
    margin: 0;
    overflow-x: hidden;
}


.container {
    padding: 20px 15px;
    margin: 0 auto;
    max-width: 1140px;
}


.asidebar {
    background-color: rgb(2, 2, 2);
    width: 200px;
    height: 100vh;
}

.asidebar_content {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    gap: 30px;
    padding: 20px;
}

.asidebar_top {
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
    text-align:left;
    padding-right: 40px;
    gap: 10px;
}


.asidebar {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    flex-wrap: wrap;
}

.asidebar ul {
    display: flex;
    flex-direction: column;
    gap: 20px;
    color: white;
}

.asidebar ul li {
    font-size: 14px;
    color: white;
    padding: 10px;
    display: flex;
    text-align: center;
    align-items: center;
    width: 100px;
    border-radius: 20px;
}

.asidebar ul li:hover {
    background-color: rgb(0, 195, 255);
    color: black;
}
</style>