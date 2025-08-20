<template>
  <section class="hero">
    <div class="container">
      <div class="hero-content">
        <!-- Text Content -->
        <div class="hero-text">
          <div class="hero-badge">
            <span class="badge-icon">🚀</span>
            <span>Trusted by 2,847+ teams worldwide</span>
          </div>
          
          <h1 class="hero-title">
            AI-Powered Project Management
            <span class="gradient-text">That Actually Works</span>
          </h1>
          
          <p class="hero-description">
            Predict project risks, optimize team performance, and deliver on time 
            with our intelligent project management platform. Join thousands of teams 
            achieving 94% project success rates.
          </p>
          
          <div class="hero-actions">
            <router-link to="/signup" class="btn btn-primary btn-large">
              <span>Start Free 14-Day Trial</span>
              <svg width="20" height="20" viewBox="0 0 20 20" fill="currentColor">
                <path fill-rule="evenodd" d="M10.293 3.293a1 1 0 011.414 0l6 6a1 1 0 010 1.414l-6 6a1 1 0 01-1.414-1.414L14.586 11H3a1 1 0 110-2h11.586l-4.293-4.293a1 1 0 010-1.414z" clip-rule="evenodd" />
              </svg>
            </router-link>
            <button @click="playDemo" class="btn btn-secondary btn-large">
              <svg width="20" height="20" viewBox="0 0 20 20" fill="currentColor">
                <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zM9.555 7.168A1 1 0 008 8v4a1 1 0 001.555.832l3-2a1 1 0 000-1.664l-3-2z" clip-rule="evenodd" />
              </svg>
              <span>Watch Demo</span>
            </button>
          </div>
          
          <div class="hero-stats">
            <div class="stat" v-for="stat in stats" :key="stat.label">
              <div class="stat-number">{{ stat.number }}</div>
              <div class="stat-label">{{ stat.label }}</div>
            </div>
          </div>
        </div>

        <!-- Visual Content -->
        <div class="hero-visual">
          <div class="dashboard-mockup">
            <div class="mockup-header">
              <div class="mockup-controls">
                <span class="control red"></span>
                <span class="control yellow"></span>
                <span class="control green"></span>
              </div>
              <div class="mockup-title">TechFlow Dashboard</div>
            </div>
            
            <div class="mockup-content">
              <DashboardPreview />
            </div>
          </div>
          
          <!-- Floating Elements -->
          <div class="floating-elements">
            <div class="floating-card card-1" :style="{ transform: `translateY(${floatingOffset}px)` }">
              <div class="card-icon success">✓</div>
              <div class="card-text">
                <div class="card-title">Project Alpha</div>
                <div class="card-subtitle">On track, 87% complete</div>
              </div>
            </div>
            
            <div class="floating-card card-2" :style="{ transform: `translateY(${-floatingOffset}px)` }">
              <div class="card-icon warning">⚠</div>
              <div class="card-text">
                <div class="card-title">Risk Detected</div>
                <div class="card-subtitle">Resource conflict in 3 days</div>
              </div>
            </div>
            
            <div class="floating-card card-3" :style="{ transform: `translateY(${floatingOffset * 0.5}px)` }">
              <div class="card-icon info">🎯</div>
              <div class="card-text">
                <div class="card-title">AI Recommendation</div>
                <div class="card-subtitle">Reassign 2 team members</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import DashboardPreview from '@/components/ui/DashboardPreview.vue'

export default {
  name: 'HeroSection',
  components: {
    DashboardPreview
  },
  data() {
    return {
      floatingOffset: 0,
      stats: [
        { number: '94%', label: 'Prediction Accuracy' },
        { number: '2,847', label: 'Active Users' },
        { number: '$2.1M', label: 'Projects Saved' }
      ]
    }
  },
  mounted() {
    this.startFloatingAnimation()
  },
  methods: {
    startFloatingAnimation() {
      const animate = () => {
        this.floatingOffset = Math.sin(Date.now() * 0.001) * 10
        requestAnimationFrame(animate)
      }
      animate()
    },
    playDemo() {
      // Handle demo video play
      console.log('Playing demo...')
    }
  }
}
</script>

<style scoped>
.hero {
  padding: 120px 0 80px;
  background: linear-gradient(135deg, var(--primary-50) 0%, white 50%, var(--gray-50) 100%);
  position: relative;
  overflow: hidden;
}

.hero::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-image: 
    radial-gradient(circle at 20% 80%, rgba(14, 165, 233, 0.1) 0%, transparent 50%),
    radial-gradient(circle at 80% 20%, rgba(14, 165, 233, 0.05) 0%, transparent 50%);
  pointer-events: none;
}

.hero-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: var(--space-16);
  align-items: center;
  position: relative;
  z-index: 1;
}

.hero-badge {
  display: inline-flex;
  align-items: center;
  gap: var(--space-2);
  padding: var(--space-2) var(--space-4);
  background: white;
  border: 1px solid var(--gray-200);
  border-radius: var(--radius-full);
  font-size: var(--font-size-sm);
  color: var(--gray-600);
  margin-bottom: var(--space-6);
  box-shadow: var(--shadow-sm);
}

.badge-icon {
  font-size: var(--font-size-base);
}

.hero-title {
  font-size: var(--font-size-5xl);
  font-weight: 800;
  line-height: 1.1;
  color: var(--gray-900);
  margin-bottom: var(--space-6);
}

.gradient-text {
  background: linear-gradient(135deg, var(--primary-600), var(--primary-700));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.hero-description {
  font-size: var(--font-size-lg);
  color: var(--gray-600);
  line-height: 1.7;
  margin-bottom: var(--space-8);
}

.hero-actions {
  display: flex;
  gap: var(--space-4);
  margin-bottom: var(--space-12);
}

.btn-large {
  padding: var(--space-4) var(--space-6);
  font-size: var(--font-size-base);
  gap: var(--space-2);
}

.btn-secondary {
  color: var(--gray-700);
  background: white;
  border: 1px solid var(--gray-300);
}

.btn-secondary:hover {
  background: var(--gray-50);
  border-color: var(--gray-400);
}

.hero-stats {
  display: flex;
  gap: var(--space-8);
}

.stat {
  text-align: center;
}

.stat-number {
  font-size: var(--font-size-2xl);
  font-weight: 700;
  color: var(--primary-600);
  line-height: 1;
}

.stat-label {
  font-size: var(--font-size-sm);
  color: var(--gray-500);
  margin-top: var(--space-1);
}

.hero-visual {
  position: relative;
}

.dashboard-mockup {
  background: white;
  border-radius: var(--radius-2xl);
  box-shadow: var(--shadow-xl);
  overflow: hidden;
  transform: perspective(1000px) rotateY(-5deg) rotateX(5deg);
  transition: transform 0.3s ease;
}

.dashboard-mockup:hover {
  transform: perspective(1000px) rotateY(-2deg) rotateX(2deg);
}

.mockup-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: var(--space-4) var(--space-6);
  background: var(--gray-50);
  border-bottom: 1px solid var(--gray-200);
}

.mockup-controls {
  display: flex;
  gap: var(--space-2);
}

.control {
  width: 12px;
  height: 12px;
  border-radius: 50%;
}

.control.red { background: #ff5f56; }
.control.yellow { background: #ffbd2e; }
.control.green { background: #27ca3f; }

.mockup-title {
  font-size: var(--font-size-sm);
  font-weight: 500;
  color: var(--gray-600);
}

.mockup-content {
  padding: var(--space-6);
  height: 400px;
}

.floating-elements {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  pointer-events: none;
}

.floating-card {
  position: absolute;
  display: flex;
  align-items: center;
  gap: var(--space-3);
  padding: var(--space-3) var(--space-4);
  background: white;
  border-radius: var(--radius-lg);
  box-shadow: var(--shadow-lg);
  border: 1px solid var(--gray-200);
  min-width: 200px;
}

.card-1 {
  top: 20%;
  right: -20px;
}

.card-2 {
  top: 60%;
  left: -20px;
}

.card-3 {
  bottom: 20%;
  right: -30px;
}

.card-icon {
  width: 32px;
  height: 32px;
  border-radius: var(--radius-lg);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: var(--font-size-sm);
  flex-shrink: 0;
}

.card-icon.success {
  background: var(--success-500);
  color: white;
}

.card-icon.warning {
  background: var(--warning-500);
  color: white;
}

.card-icon.info {
  background: var(--primary-500);
  color: white;
}

.card-title {
  font-size: var(--font-size-sm);
  font-weight: 600;
  color: var(--gray-900);
}

.card-subtitle {
  font-size: var(--font-size-xs);
  color: var(--gray-500);
}

@media (max-width: 1024px) {
  .hero-content {
    grid-template-columns: 1fr;
    gap: var(--space-12);
    text-align: center;
  }
  
  .hero-title {
    font-size: var(--font-size-4xl);
  }
  
  .floating-elements {
    display: none;
  }
}

@media (max-width: 768px) {
  .hero {
    padding: 100px 0 60px;
  }
  
  .hero-title {
    font-size: var(--font-size-3xl);
  }
  
  .hero-actions {
    flex-direction: column;
    align-items: center;
  }
  
  .hero-stats {
    justify-content: center;
    gap: var(--space-6);
  }
  
  .dashboard-mockup {
    transform: none;
  }
}
</style>