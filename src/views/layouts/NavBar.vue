<script setup>
import router from '@/router';
import { RouterLink } from 'vue-router'

const logOut = async () => {
    localStorage.clear()
    await router.push({ name: 'signin' })
}

</script>

<template>
    <nav class="navbar navbar-expand-lg navbar-dark shadow" style="background: #ff006a ">
        <div class="container">
            <RouterLink :to="{ name: 'home' }" class="navbar-brand">Marionette_Genetics</RouterLink>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent"
                aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <ul class="navbar-nav ms-auto mb-2 mb-lg-0">
                    <li class="nav-item">
                        <RouterLink :to="{ name: 'home' }" class="nav-link active" aria-current="page"><i
                                class="bi bi-house-fill me-1"></i>Home page</RouterLink>
                    </li>
                    <li class="nav-item">
                        <router-link :to="{ name: 'signin' }" class="nav-link" href="#"><i
                                class="bi bi-bank me-1"></i>Login</router-link>
                    </li>

                    <li class="nav-item dropdown">
                        <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown"
                            aria-expanded="false">
                            <i class="bi bi-bank2 me-1"></i>Cannabis strain
                        </a>

                        <ul class="dropdown-menu">
                            <li>
                                <RouterLink :to="{ name: 'wonders' }" class="dropdown-item">Cannabis
                                </RouterLink>
                            </li>
                            <li>
                                <RouterLink :to="{ name: 'add-wonder' }" class="dropdown-item">Add Cannabis Recommend
                                </RouterLink>
                            </li>
                            <li><a class="dropdown-item" href="#">Update Cannabis</a></li>
                            <li><a class="dropdown-item" href="#">Delete Cannabis</a></li>
                            <li>
                                <hr class="dropdown-divider">
                            </li>
                            <li><a class="dropdown-item" href="http://localhost:5173/">Marionette_Genetics_Website</a></li>
                        </ul>
                    </li>

                    <li class="nav-item dropdown">
                        <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown"
                            aria-expanded="false">
                            <i class="bi bi-bank2 me-1"></i>About me
                        </a>
                        <ul class="dropdown-menu">
                            <li><a class="dropdown-item" href="#">History</a></li>
                            <li>
                                <RouterLink :to="{ name: 'about' }" class="dropdown-item">Mindset</RouterLink>
                            </li>
                            <li><a class="dropdown-item" href="#">Member</a></li>
                            <li><a class="dropdown-item" href="#">Maps</a></li>
                            <li>
                                <hr class="dropdown-divider">
                            </li>
                            <li><a class="dropdown-item" href="#">Contact me</a></li>
                        </ul>
                    </li>

                    <li class="nav-item dropdown">
                        <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown"
                            aria-expanded="false">
                            Course
                        </a>
                        <ul class="dropdown-menu">
                            <li><a class="dropdown-item"
                                    href="https://bsq.vec.go.th/th-th/%E0%B8%AB%E0%B8%A5%E0%B8%B1%E0%B8%81%E0%B8%AA%E0%B8%B9%E0%B8%95%E0%B8%A3/%E0%B8%9B%E0%B8%A3%E0%B8%B0%E0%B8%81%E0%B8%B2%E0%B8%A8%E0%B8%99%E0%B8%B5%E0%B8%A2%E0%B8%9A%E0%B8%B1%E0%B8%95%E0%B8%A3%E0%B8%A7%E0%B8%B4%E0%B8%8A%E0%B8%B2%E0%B8%8A%E0%B8%B5%E0%B8%9E(%E0%B8%9B%E0%B8%A7%E0%B8%8A)/%E0%B8%AB%E0%B8%A5%E0%B8%B1%E0%B8%81%E0%B8%AA%E0%B8%B9%E0%B8%95%E0%B8%A3%E0%B8%9E%E0%B8%A82562(%E0%B8%9B%E0%B8%A3%E0%B8%B1%E0%B8%9A%E0%B8%9B%E0%B8%A3%E0%B8%B8%E0%B8%87%E0%B8%9E%E0%B8%A82565).aspx"
                                    target="_blank">Vocational Certificate</a></li>
                            <li><a class="dropdown-item"
                                    href="https://bsq.vec.go.th/th-th/%E0%B8%AB%E0%B8%A5%E0%B8%B1%E0%B8%81%E0%B8%AA%E0%B8%B9%E0%B8%95%E0%B8%A3/%E0%B8%9B%E0%B8%A3%E0%B8%B0%E0%B8%81%E0%B8%B2%E0%B8%A8%E0%B8%99%E0%B8%B5%E0%B8%A2%E0%B8%9A%E0%B8%B1%E0%B8%95%E0%B8%A3%E0%B8%A7%E0%B8%B4%E0%B8%8A%E0%B8%B2%E0%B8%8A%E0%B8%B5%E0%B8%9E%E0%B8%8A%E0%B8%B1%E0%B9%89%E0%B8%99%E0%B8%AA%E0%B8%B9%E0%B8%87(%E0%B8%9B%E0%B8%A7%E0%B8%AA)/%E0%B8%AB%E0%B8%A5%E0%B8%B1%E0%B8%81%E0%B8%AA%E0%B8%B9%E0%B8%95%E0%B8%A3%E0%B8%9E%E0%B8%A82563(%E0%B8%9B%E0%B8%A3%E0%B8%B1%E0%B8%9A%E0%B8%9B%E0%B8%A3%E0%B8%B8%E0%B8%87%E0%B8%9E%E0%B8%A82565).aspx"
                                    target="_blank">Higher Vocational Certificate</a></li>
                            <li><a class="dropdown-item"
                                    href="https://bsq.vec.go.th/th-th/%E0%B8%AB%E0%B8%A5%E0%B8%B1%E0%B8%81%E0%B8%AA%E0%B8%B9%E0%B8%95%E0%B8%A3/%E0%B8%9B%E0%B8%A3%E0%B8%B4%E0%B8%8D%E0%B8%8D%E0%B8%B2%E0%B8%95%E0%B8%A3%E0%B8%B5/%E0%B8%9E%E0%B8%B8%E0%B8%97%E0%B8%98%E0%B8%A8%E0%B8%B1%E0%B8%81%E0%B8%A3%E0%B8%B2%E0%B8%8A2564.aspx"
                                    target="_blank">Bachelor's degree</a></li>
                            <li>
                                <hr class="dropdown-divider">
                            </li>
                            <li><a class="dropdown-item"
                                    href="https://bsq.vec.go.th/th-th/%e0%b8%ab%e0%b8%99%e0%b9%89%e0%b8%b2%e0%b8%ab%e0%b8%a5%e0%b8%b1%e0%b8%81.aspx"
                                    target="_blank">More Course</a></li>
                        </ul>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#">More Web site</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#" @click="logOut"><i
                                class="bi bi-box-arrow-right me-1"></i>Log Out</a>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Sarabun&display=swap');

.navbar {
    font-family: 'Sarabun', sans-serif;
}
</style>
