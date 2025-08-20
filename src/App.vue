<template>
  <div id="app">
    <AppHeader />
    <router-view />
    <AppFooter />

     <Vue3Marquee class="team-marquee">
        <div class="team-grid">
          <div class="team-member" v-for="member in teamMembers" :key="member.id">
            <div class="member-avatar">
               <img v-if="member.avatar" :src="require(`@/assets/team/${member.avatar}`)" alt="Avatar of {{ member.name }}"/>
            </div>
            <div class="member-info">
              <h3>{{ member.name }}</h3>
              <p class="member-role">{{ member.role }}</p>
              <p class="member-description">{{ member.description }}</p>
              <div class="member-social">
                <a href="#" class="social-link">LinkedIn</a>
                <a href="#" class="social-link">Twitter</a>
              </div>
            </div>
          </div>
        </div>
      </Vue3Marquee>
  </div>
</template>

<script>
import AppHeader from '@/components/layout/AppHeader.vue'
import AppFooter from '@/components/layout/AppFooter.vue'
import { Vue3Marquee } from 'vue3-marquee'

export default {
  name: 'App',
  components: {
    AppHeader,
    AppFooter,
    Vue3Marquee
  },

  data() {
    return {
      teamMembers: []
    }
  },
  mounted() {
    this.teamMembers = [
      {
        id: 1,
        name: 'Sarah Chen',
        role: 'CEO & Co-Founder',
        avatar: 'avatar.jpeg',
        description: 'Former VP of Engineering at Microsoft. 15+ years building enterprise software solutions.'
      },
      {
        id: 2,
        name: 'Marcus Rodriguez',
        role: 'CTO & Co-Founder',
        avatar: 'avatar.jpeg',
        description: 'AI/ML expert with PhD from Stanford. Previously led data science teams at Google and Meta.'
      },
      {
        id: 3,
        name: 'Emily Johnson',
        role: 'Head of Product',
        avatar: 'avatar.jpeg',
        description: 'Former Slack product lead with a passion for user experience and product innovation.'
      },
      {
        id: 4,
        name: 'David Kim',
        role: 'Head of Engineering',
        avatar: 'avatar.jpeg',
        description: 'Full-stack architect who has built scalable platforms serving millions of users.'
      },
      {
        id: 5,
        name: 'Aisha Patel',
        role: 'Marketing Director',
        avatar: 'avatar.jpeg',
        description: 'Digital marketing strategist with a track record of growing tech startups.'
      },
      {
        id: 6,
        name: 'John Smith',
        role: 'UI/UX Designer',
        avatar: 'avatar.jpeg',
        description: 'Creative designer with a focus on intuitive user interfaces and engaging experiences.'
      }
    ]
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap');

:root {
  /* Colors */
  --primary-50: #f0f9ff;
  --primary-100: #e0f2fe;
  --primary-500: #0ea5e9;
  --primary-600: #0284c7;
  --primary-700: #0369a1;
  --primary-900: #0c4a6e;
  
  --gray-50: #f9fafb;
  --gray-100: #f3f4f6;
  --gray-200: #e5e7eb;
  --gray-300: #d1d5db;
  --gray-400: #9ca3af;
  --gray-500: #6b7280;
  --gray-600: #4b5563;
  --gray-700: #374151;
  --gray-800: #1f2937;
  --gray-900: #111827;
  
  --success-500: #10b981;
  --warning-500: #f59e0b;
  --error-500: #ef4444;
  
  /* Typography */
  --font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
  --font-size-xs: 0.75rem;
  --font-size-sm: 0.875rem;
  --font-size-base: 1rem;
  --font-size-lg: 1.125rem;
  --font-size-xl: 1.25rem;
  --font-size-2xl: 1.5rem;
  --font-size-3xl: 1.875rem;
  --font-size-4xl: 2.25rem;
  --font-size-5xl: 3rem;
  --font-size-6xl: 3.75rem;
  
  /* Spacing */
  --space-1: 0.25rem;
  --space-2: 0.5rem;
  --space-3: 0.75rem;
  --space-4: 1rem;
  --space-5: 1.25rem;
  --space-6: 1.5rem;
  --space-8: 2rem;
  --space-10: 2.5rem;
  --space-12: 3rem;
  --space-16: 4rem;
  --space-20: 5rem;
  --space-24: 6rem;
  
  /* Shadows */
  --shadow-sm: 0 1px 2px 0 rgb(0 0 0 / 0.05);
  --shadow-md: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);
  --shadow-lg: 0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1);
  --shadow-xl: 0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 / 0.1);
  
  /* Border Radius */
  --radius-sm: 0.125rem;
  --radius-md: 0.375rem;
  --radius-lg: 0.5rem;
  --radius-xl: 0.75rem;
  --radius-2xl: 1rem;
  --radius-full: 9999px;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: var(--font-family);
  font-size: var(--font-size-base);
  line-height: 1.6;
  color: var(--gray-800);
  background-color: #ffffff;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 var(--space-6);
}
@media (max-width: 768px) {
  .container {
    padding: 0 var(--space-4);
  }
}

.team-marquee {
  overflow: hidden;
  width: 100%;
  background: var(--primary-50);
  padding: var(--space-6) 0;
}
.team-grid {
  display: flex;
  gap: var(--space-8);
  padding: var(--space-6) var(--space-6);
  margin-top: 4rem;
}
.team-member {
  background-color: #f0f0f0;
  border-radius: 8px;
  padding: 1rem;
  width: 230px;
  text-align: center;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  min-height: 300px;
}
.member-avatar {
  margin-bottom: var(--space-6);
}
.member-avatar img {
  width: 90px;
  height: 90px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto;
}
.member-info h3 {
  font-size: var(--font-size-lg);
  font-weight: 600;
  color: var(--gray-900);
  margin-bottom: var(--space-2);
}
.member-role {
  color: var(--primary-600);
  font-weight: 500;
  margin-bottom: var(--space-4);
}
.member-description {
  color: var(--gray-600);
  line-height: 1.5;
  margin-bottom: var(--space-4);
}
.member-social {
  display: flex;
  justify-content: center;
  gap: var(--space-4);
}
.social-link {
  color: var(--primary-500);
  text-decoration: none;
  font-weight: 500;
  transition: color 0.2s ease;
}
.social-link:hover {
  color: var(--primary-700);
}
</style>
