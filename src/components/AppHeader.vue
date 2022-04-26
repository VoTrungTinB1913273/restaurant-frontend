<template>
    <nav class="navbar navbar-expand-lg navbar-light bg-secondary">
        <a href="/" class="navbar-brand">Website Search Restaurant</a>
        <div class="mr-auto navbar-nav">
            <li class="nav-item">
                <router-link :to="{ name: 'restaurant' }" class="nav-link">
                    Trang chủ
                    <i class="fas fa-map"></i>
                </router-link>
            </li>
            <li class="nav-item">
                <router-link :to="{ name: 'menu' }" class="nav-link">
                    Menu
                    <i class="fas fa-bars"></i>
                </router-link>
            </li>
        </div>
    </nav>
</template>