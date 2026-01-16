<template>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Survival Portfolio | Ashlee Dan Esprecion</title>
    <link rel="stylesheet" href=".../css/Personalprofile.css">
    <link href="https://fonts.googleapis.com/css2?family=Special+Elite&family=Oswald:wght@700&family=Inter:wght@400;700&display=swap" rel="stylesheet">
    <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
</head>
<body>

    <div id="app">
        <header>
            <nav class="navbar">
                <div class="logo">SURVIVOR_LOG: ASHLEE</div>
                <ul class="nav-links">
                    <li><a href="#home">Safe Zone</a></li>
                    <li><a href="#about">The Records</a></li>
                    <li><a href="#creations">The Vision</a></li>
                    <li><a href="#guestbook">The Comms</a></li>
                </ul>
            </nav>
        </header>

        <section id="home" class="hero">
            <div class="hero-content">
                <h5 class="stamped">Entry #2026</h5>
                <h1>Ashlee Dan Esprecion</h1>
                <p class="subtitle">UI/UX DESIGNER | STORYTELLER | SURVIVOR</p>
                <a href="#about" class="btn-primary">View Records</a>
            </div>
        </section>

        <section id="about" class="container">
            <div class="section-header">
                <h2 class="grunge-text">Personnel File</h2>
                <hr class="blood-line">
            </div>
            <div class="about-flex">
                <div class="about-text">
                    <p>Second year IT student at APC. Specializing in interfaces that evoke emotion. Highly inspired by the choice-driven narrative of Telltale's "The Walking Dead."</p>
                    
                    <div class="education-simple survival-box">
                        <h3 class="gold-text">TRAINING HISTORY</h3>
                        <div class="edu-item">
                            <strong>BS Information Technology</strong>
                            <span>Asia Pacific College | 2024 - Present</span>
                        </div>
                    </div>
                </div>

                <div class="skills-contact-box survival-card">
                    <h3 class="box-title">Contact Frequency</h3>
                    <p class="contact-label">ENCRYPTED EMAIL:</p>
                    <p class="contact-data">adesprecion@student.apc.edu.ph</p>
                    
                    <p class="contact-label">HQ LOCATION:</p>
                    <p class="contact-data">3 Humabon, Makati, 1232</p>
                    
                    <hr class="dark-hr">

                    <h3 class="box-title">Survival Skills</h3>
                    <div class="skill-tag" v-for="skill in skills">{{ skill }}</div>
                </div>
            </div>
        </section>

        <section id="creations" class="container">
            <div class="section-header">
                <h2 class="grunge-text">Visual Intel</h2>
                <hr class="blood-line">
            </div>
            
            <div class="carousel-container">
                <div v-for="(img, index) in gallery" :key="index" class="carousel-item" @click="openLightbox(img.url)">
                    <img :src="img.url">
                    <div class="overlay"><span>{{ img.title }}</span></div>
                </div>
            </div>
        </section>

        <section id="guestbook" class="container" style="background: #0a0a0a;">
            <div class="section-header">
                <h2 class="grunge-text">Broadcast Signal</h2>
                <p style="color: #666; font-family: 'Special Elite';">Leave a message in the comms log.</p>
                <hr class="blood-line">
            </div>

            <div class="guestbook-container">
                <form @submit.prevent="addComment" class="comment-form">
                    <input v-model="newComment.name" type="text" placeholder="ID Name..." required>
                    <textarea v-model="newComment.text" placeholder="Type your transmission..." required></textarea>
                    <button type="submit" class="btn-primary danger-btn">Send Signal</button>
                </form>

                <div class="comments-list">
                    <div v-for="(c, i) in comments" :key="i" class="comment-item survival-card">
                        <strong class="gold-text">{{ c.name }}</strong>
                        <p class="typewriter">{{ c.text }}</p>
                    </div>
                </div>
            </div>
        </section>

        <section id="resources" class="container" style="text-align: center;">
            <div class="resources-grid">
                <div class="resource-item">
                    <p class="res-title">Imagery</p>
                    <p class="res-desc">AMC TWD Gallery</p>
                </div>
                <div class="resource-item">
                    <p class="res-title">Fonts</p>
                    <p class="res-desc">Special Elite & Oswald</p>
                </div>
            </div>
        </section>

        <div v-if="activeImg" class="vue-lightbox" @click="activeImg = null">
            <span class="close">&times;</span>
            <img :src="activeImg">
        </div>

        <footer>
            <p>ENTRY LOG: 2026 | BUILT BY ASHLEE DAN ESPRECION</p>
        </footer>
    </div>

    <script>
        const { createApp } = Vue
        createApp({
            data() {
                return {
                    activeImg: null,
                    skills: ['HTML', 'CSS', 'VUE.JS', 'UI DESIGN'],
                    gallery: [
                        { title: 'TWD TV Series', url: 'https://i.pinimg.com/1200x/c4/dd/40/c4dd40e6c191da0958195424b3fa6f9c.jpg' },
                        { title: 'Telltale Games', url: 'https://i.pinimg.com/736x/e0/70/b5/e070b52773a9ce6344b7087e7c0653d0.jpg' },
                        { title: 'The Vision', url: 'https://i.pinimg.com/736x/87/4e/21/874e218718a1a8e6894de74ff9622781.jpg' }
                    ],
                    newComment: { name: '', text: '' },
                    comments: []
                }
            },
            mounted() {
                // LOAD COMMENTS FROM LOCAL STORAGE
                const savedComments = localStorage.getItem('survivorComments');
                if (savedComments) {
                    this.comments = JSON.parse(savedComments);
                } else {
                    this.comments = [{ name: 'Command', text: 'Waiting for signal...' }];
                }
            },
            methods: {
                openLightbox(url) { this.activeImg = url; },
                addComment() {
                    this.comments.unshift({...this.newComment});
                    // SAVE TO LOCAL STORAGE
                    localStorage.setItem('survivorComments', JSON.stringify(this.comments));
                    this.newComment.name = '';
                    this.newComment.text = '';
                }
            }
        }).mount('#app')
    </script>
</body>

</body>
</template>
<script></script>
<style src = "./css/Personalprofile.css"></style>