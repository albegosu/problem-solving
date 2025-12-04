<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

// Import images (uncomment when you add them to assets folder)
// Hero image is now loaded via CSS variable in style.css
import methodologyImage from './assets/methodology.png'
import einsteinImage from './assets/einstein.png'
// import munariImage from './assets/munari-method.svg'

const isVisible = ref(false)
const showBackToTop = ref(false)

onMounted(() => {
  setTimeout(() => {
    isVisible.value = true
  }, 100)
  
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})

const handleScroll = () => {
  showBackToTop.value = window.scrollY > 500
}

const scrollToSection = (sectionId) => {
  const element = document.getElementById(sectionId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}

const scrollToTop = () => {
  window.scrollTo({ top: 0, behavior: 'smooth' })
}

const scrollToNextSection = (currentSection) => {
  const sections = ['intro', 'methodology', 'creativity', 'munari', 'problem-method', 'proactivity']
  const currentIndex = sections.indexOf(currentSection)
  if (currentIndex < sections.length - 1) {
    scrollToSection(sections[currentIndex + 1])
  }
}
</script>

<template>
  <div class="app">
    <!-- Hero Section -->
    <section class="hero" :class="{ 'fade-in': isVisible }">
      <div class="container">
        <!-- Hero image is now a background with color overlay -->
        <h1 class="hero-title">Got problems?</h1>
        <p class="hero-subtitle">Methodology for survival</p>
        <button class="cta-button" @click="scrollToSection('intro')">
          Let's begin?
        </button>
      </div>
      <div class="scroll-indicator">
        <span>↓</span>
      </div>
    </section>

    <!-- Introduction Section -->
    <section id="intro" class="section intro-section">
      <div class="container">
        <h2 class="section-title">How do we face problems?</h2>
        <div class="problem-flow">
            <div class="flow-item">
              <span class="flow-emoji">🤐</span>
              <p class="flow-item-text">
                I have a problem <br>
                <span class="arrow">↓</span> <br>
                I don't say it <br>
                <span class="arrow">↓</span> <br>
                It becomes entrenched</p>
              <small>(Fear, indecision, culture of silence)</small>
            </div>
            <div class="flow-item">
              <span class="flow-emoji">💬</span>
              <p class="flow-item-text">
                I say it <br>
                <span class="arrow">↓</span> <br>
                I only verbalize it, I don't start solving it</p>
                <small>(Complaint, noise, not digging into the problem)</small>
            </div>
        </div>
        <div class="highlight-box">
            What's more common in the team: not saying the problem or saying it without progressing?
        </div>
        <button class="next-section-btn" @click="scrollToNextSection('intro')" aria-label="Next section">
          ↓
        </button>
      </div>
    </section>

    <!-- Methodology Section -->
    <section id="methodology" class="section methodology-section">
      <!-- Methodology image positioned at left -->
      <div class="section-image-left">
        <img :src="methodologyImage" alt="Design methodology" />
      </div>
      
      <div class="container">
        <h2 class="section-title">Focused on: <br>
          <span class="section-title-small">Design Methodology</span></h2>
        
        <div class="methodology-grid">
          <div class="methodology-card">
            <h3>'How are objects born?'</h3>
            <span class="arrow">↓</span>
            <h3>Bruno Munari</h3>
          </div>
          <div class="methodology-card">
            <h4>Project Methodology</h4>
            <p>Structured process</p>
          </div>
          <div class="methodology-card">
            <h4>Design Thinking</h4>
            <p>Understand the problem, generate alternatives and test solutions</p>
          </div>
        </div>
        <button class="next-section-btn" @click="scrollToNextSection('methodology')" aria-label="Next section">
          ↓
        </button>
      </div>
    </section>

    <!-- Creativity Section -->
    <section id="creativity" class="section creativity-section">
      <!-- Einstein image positioned at right -->
      <div class="section-image-right">
        <img :src="einsteinImage" alt="Einstein" />
      </div>
      
      <div class="container">
        <h2 class="section-title">The romantic idea of creativity</h2>
        <blockquote class="quote">
          "When we talk about solving problems, we usually think of intuition, experience or improvisation. 
          But Bruno Munari reminds us that 
          <span class="quote-stroke">any process
          <span class="quote-stroke-span">—from designing an object to developing software— </span>
          improves when we abandon the romantic idea of 'genius' and adopt a clear method..."</span> 
        </blockquote>
        <div class="question-box">
          <p class="italic">Is creativity only for art?</p>
        </div>
        <button class="next-section-btn" @click="scrollToNextSection('creativity')" aria-label="Next section">
          ↓
        </button>
      </div>
    </section>

    <!-- Munari Applied Section -->
    <section id="munari" class="section munari-section">
      <div class="container">
        <h2 class="section-title">Munari applied to software</h2>
        
        <!-- Uncomment when you add munari image to assets -->
        <!-- <div class="section-image">
          <img :src="munariImage" alt="Munari method" />
        </div> -->
        
        <div class="principles">
          <div class="principle-item">
            <div>
              <strong>Demystify creativity</strong> <br>
              We're not looking for geniuses. We expect to achieve reproducible processes
            </div>
          </div>
          <div class="principle-item">
            <div>
              <strong>Design is an orderly way to solve problems</strong> <br>
              Just like writing a feature, refactoring, or fixing a bug
            </div>
          </div>
        </div>
        
        <div class="method-box">
          <h3>Munari's basic method (ultra summarized):</h3>
          <ol class="method-steps">
            <li>Define the problem</li>
            <li>Analyze context</li>
            <li>Generate options → Transfer the doubt/need</li>
            <li>Prototype</li>
            <li>Evaluate</li>
            <li>Select the simplest and most effective solution</li>
          </ol>
          <p class="method-quote">"Method as an antidote to the drama of the problem."</p>
        </div>
        <button class="next-section-btn" @click="scrollToNextSection('munari')" aria-label="Next section">
          ↓
        </button>
      </div>
    </section>

    <!-- From Problem to Method Section -->
    <section id="problem-method" class="section problem-method-section">
      <div class="container">
        <h2 class="section-title">"From problem to method"</h2>
        
        <div class="method-flow">
          <div class="method-step">
            <div class="step-number">1</div>
            <h3 class="step-title">Examples</h3>
            <ul class="step-list">
              <li>"I don't understand the acceptance criteria for my task."</li>
              <li>"There's friction between two teams."</li>
              <li>"I don't have clarity on priorities."</li>
            </ul>
          </div>

          <div class="flow-arrow">↓</div>

          <div class="method-step">
            <div class="step-number">2</div>
            <h3 class="step-title">Redefine</h3>
            <ul class="step-list">
              <li>What is the real problem?</li>
              <li>What conditions surround it?</li>
              <li>What part is ambiguous?</li>
              <li>What would be a clear, concrete, neutral definition of the problem?</li>
            </ul>
          </div>

          <div class="flow-arrow">↓</div>

          <div class="method-step">
            <div class="step-number">3</div>
            <h3 class="step-title">Generate paths</h3>
            <ul class="step-list">
              <li>Not complete solutions</li>
              <li>Only alternatives</li>
              <li>Options that lead to options</li>
            </ul>
            <p class="step-note">Munari insisted that creativity arises when there is variety, not when we look for the "perfect answer" at first.</p>
          </div>
        </div>

        <button class="next-section-btn" @click="scrollToNextSection('problem-method')" aria-label="Next section">
          ↓
        </button>
      </div>
    </section>

    <!-- Proactivity Section -->
    <section id="proactivity" class="section proactivity-section">
      <div class="container">
        <h2 class="section-title">Proactivity ≠ spontaneity</h2>
        <div class="proactivity-content">
          <div class="proactivity-item">
            <span class="icon">🎯</span>
            <p>Initiative is not acting without thinking, but starting a conscious process.</p>
          </div>
          <div class="proactivity-item">
            <span class="icon">💻</span>
            <p>In technology, where problems are constant, design as a method is an extremely powerful tool.</p>
          </div>
          <div class="proactivity-item">
            <span class="icon">🔄</span>
            <p>A problem begins to be solved when it stops being a drama and becomes a process.</p>
          </div>
        </div>
        
        <div class="final-message">
          <h3>We're not looking for heroes who solve problems, but teams that know how to design solutions.</h3>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
      <div class="container">
        <p>Problem solving methodology</p>
        <p class="instagram-link">
          <a href="https://dash.resiz.es/" target="_blank" rel="noopener noreferrer">
            See more in my PRO plan 'Surviving Resizes' →
          </a>
        </p>
      </div>
    </footer>

    <!-- Back to Top Button -->
    <transition name="fade">
      <button 
        v-if="showBackToTop" 
        class="back-to-top"
        @click="scrollToTop"
        aria-label="Back to top"
      >
        ↑
      </button>
    </transition>
  </div>
</template>

<style scoped>
.app {
  width: 100%;
  overflow-x: hidden;
}

/* Hero Section */
.hero {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background: var(--color-background);
  color: var(--color-text-primary);
  position: relative;
  opacity: 0;
  transform: translateY(20px);
  transition: all 1s ease-out;
}

/* Hero background image with color overlay */
.hero::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-image: var(--hero-bg-image);
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  opacity: 0.15;
  z-index: 0;
  filter: grayscale(100%);
}

.hero .container {
  position: relative;
  z-index: 1;
  align-items: center;
}

.hero-image {
  display: none;
}

.hero-image img {
  width: 100%;
  height: auto;
  display: block;
}

@keyframes float {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-20px);
  }
}

.hero.fade-in {
  opacity: 1;
  transform: translateY(0);
}

.hero-title {
  font-family: 'Oswald', sans-serif;
  font-size: 4rem;
  font-weight: 400;
  margin: 0;
  text-align: center;
  line-height: 1.1;
  margin-bottom: 1rem;
  letter-spacing: 0.02em;
  text-transform: uppercase;
}

.hero-subtitle {
  font-style: italic;
  font-size: 1.5rem;
  font-weight: 300;
  margin: 0;
  opacity: 0.9;
  margin-bottom: 2rem;
  text-align: center;
}

.cta-button {
  background: transparent;
  color: var(--color-text);
  border: 2px solid var(--color-text);
  padding: 1rem 2.5rem;
  font-size: 1rem;
  font-weight: 400;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.3s ease;
  letter-spacing: 0.05em;
  align-self: center;
  width: auto;
}

.cta-button:hover {
  background: var(--color-text);
  color: var(--color-background);
}

.scroll-indicator {
  position: absolute;
  bottom: 2rem;
  animation: bounce 2s infinite;
}

.scroll-indicator span {
  font-size: 2rem;
}

@keyframes bounce {
  0%, 20%, 50%, 80%, 100% {
    transform: translateY(0);
  }
  40% {
    transform: translateY(-20px);
  }
  60% {
    transform: translateY(-10px);
  }
}

/* Common Section Styles */
.section {
  padding: 5rem 2rem;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  position: relative;
}

.section:nth-child(even) {
  background: var(--color-background);
}

.section:nth-child(odd) {
  background: var(--color-background);
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  width: 100%;
  padding: 0 1rem;
  text-align: center;
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

/* Section Images */
.section-image {
  max-width: 600px;
  margin: 0 auto 3rem;
  padding: 2rem;
  background: var(--color-background-alt);
  border-radius: 12px;
  border: 1px solid var(--color-border);
}

.section-image img {
  width: 100%;
  height: auto;
  display: block;
  border-radius: 8px;
  filter: grayscale(100%);
  opacity: 0.9;
}

/* Section Images - Left Aligned (No Box) */
.section-image-left {
  position: absolute;
  left: 0;
  top: 50%;
  transform: translateY(-50%);
  max-width: 500px;
  width: 35vw;
  padding: 0;
  margin: 0;
  z-index: 0;
}

.section-image-left img {
  width: 100%;
  height: auto;
  display: block;
  filter: grayscale(100%);
  opacity: 0.4;
}

/* Section Images - Right Aligned (No Box) */
.section-image-right {
  position: absolute;
  right: 0;
  bottom: 0;
  height: 100%;
  width: auto;
  padding: 0;
  margin: 0;
  z-index: 0;
}

.section-image-right img {
  height: 100%;
  width: auto;
  display: block;
  filter: grayscale(100%);
  opacity: 0.3;
  object-fit: cover;
}

.section-title {
  font-family: 'Oswald', sans-serif;
  font-style: normal;
  font-size: 2.5rem;
  font-weight: 400;
  margin-bottom: 3rem;
  text-align: center;
  color: var(--color-text-primary);
  letter-spacing: 0.03em;
  position: relative;
  z-index: 1;
  text-transform: uppercase;
}

/* Introduction Section */
.problem-flow {
  display: flex;
  gap: 1.5rem;
  margin-bottom: 3rem;
  max-width: 900px;
  margin-left: auto;
  margin-right: auto;
  align-items: stretch;
}

.flow-item {
  background: var(--color-background-alt);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  padding: 2rem;
  border-radius: 12px;
  border: 1px solid var(--color-border);
  transition: all 0.3s ease;
  text-align: left;
  flex: 1;
  min-width: 0;
  min-height: 300px;
}

.flow-item:hover {
  border-color: var(--color-text);
}

.flow-item-text {
  text-align: center;
}

.flow-emoji {
  font-size: 2rem;
  display: block;
  margin-bottom: 1rem;
}

.flow-item p {
  font-size: 1.1rem;
  color: var(--color-text-primary);
  margin: 0.5rem 0;
  font-weight: 300;
  line-height: 1.6;
}

.flow-item small {
  color: var(--color-text-muted);
  font-style: italic;
  font-size: 0.9rem;
  margin-top: auto;
  display: block;
  padding-top: 1rem;
}

.quote-stroke {
  color: var(--color-text);
  font-weight: 600;
  font-style: bold;
}

.quote-stroke-span {
  color: var(--color-text);
  font-weight: 100;
}

.flow-separator {
  text-align: center;
  font-size: 1.2rem;
  font-weight: 300;
  color: var(--color-text-muted);
}

.section-title-small {
  color: var(--color-text);
  font-weight: 300;
  text-transform: none;
}

.highlight-box {
  background: var(--color-background-alt);
  color: var(--color-text-primary);
  padding: 3rem;
  border-radius: 12px;
  text-align: center;
  max-width: 1300px;
  margin-left: auto;
  margin-right: auto;
  border: 1px solid var(--color-border);
}

.highlight-box h3 {
  font-size: 2rem;
  margin-bottom: 1rem;
  font-weight: 400;
  color: var(--color-text);
}

.highlight-box p {
  font-size: 1.1rem;
  line-height: 1.7;
  margin-bottom: 1.5rem;
  font-weight: 300;
  color: var(--color-text-primary);
}

.question {
  font-style: italic;
  font-size: 1.1rem;
  margin-top: 1.5rem;
  padding-top: 1.5rem;
  border-top: 1px solid var(--color-border);
  color: var(--color-text-secondary);
}

/* Methodology Section */
.methodology-section {
  position: relative;
}

.methodology-section .container {
  position: relative;
}

.methodology-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  max-width: 1000px;
  margin: 0 auto;
  position: relative;
  z-index: 1;
}

.methodology-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background: var(--color-background-alt);
  padding: 2rem;
  border-radius: 12px;
  border: 1px solid var(--color-border);
  text-align: center;
  transition: all 0.3s ease;
}

.methodology-card:hover {
  border-color: var(--color-text);
}

.methodology-card.highlighted {
  background: var(--color-background-alt);
  color: var(--color-text-primary);
  border-color: var(--color-text);
}

.methodology-card h3 {
  font-size: 1.2rem;
  margin-bottom: 0.5rem;
  font-weight: 400;
  color: var(--color-text-primary);
}

.methodology-card h4 {
  font-size: 1.4rem;
  margin-bottom: 1rem;
  font-weight: 400;
  color: var(--color-text);
}

.methodology-card p {
  font-weight: 300;
  color: var(--color-text-secondary);
}

.methodology-card.highlighted h4 {
  color: var(--color-text);
}

.methodology-card.highlighted p {
  color: var(--color-text-primary);
}

.arrow {
  font-size: 1.5rem;
  color: var(--color-text);
  font-weight: 300;
}

/* Creativity Section */
.creativity-section {
  background: var(--color-background);
  color: var(--color-text-primary);
}

.creativity-section .container {
  padding-top: 5rem;
  max-width: 700px;
}

.creativity-section .section-title {
  color: var(--color-text-primary);
  text-align: right;
  max-width: 100%;
}

.quote {
  font-size: 1.2rem;
  line-height: 1.8;
  font-style: italic;
  padding: 2rem;
  background: rgba(54, 70, 79, 0.9);
  border-left: 3px solid var(--color-text);
  border-right: none;
  border-radius: 8px;
  margin-bottom: 2rem;
  max-width: 100%;
  text-align: right;
  font-weight: 300;
  color: var(--color-text-secondary);
  backdrop-filter: blur(5px);
}

.question-box {
  text-align: right;
  font-size: 1.3rem;
  margin-top: 2rem;
  padding: 1.5rem;
  background: rgba(54, 70, 79, 0.9);
  border-radius: 8px;
  max-width: 100%;
  backdrop-filter: blur(5px);
}

.question-box p {
  color: var(--color-text);
}

.italic {
  font-style: italic;
  font-weight: 300;
}

/* Munari Section */
.principles {
  margin-bottom: 3rem;
  text-align: center;
  max-width: 900px;
  margin-left: auto;
  margin-right: auto;
}

.principle-item {
  display: flex;
  justify-content: center;
  margin-bottom: 1.5rem;
  font-size: 1.05rem;
  line-height: 1.7;
  font-weight: 300;
  color: var(--color-text-secondary);
}

.principle-item div {
  text-align: center;
}

.principle-item strong {
  font-weight: 400;
  color: var(--color-text);
}

.bullet {
  color: var(--color-text);
  font-size: 1.5rem;
  font-weight: 400;
}

.method-box {
  background: var(--color-background-alt);
  padding: 3rem;
  border-radius: 12px;
  border: 1px solid var(--color-border);
  max-width: 900px;
  margin-left: auto;
  margin-right: auto;
  text-align: left;
}

.method-box h3 {
  color: var(--color-text);
  margin-bottom: 1.5rem;
  font-weight: 400;
  font-size: 1.3rem;
}

.method-steps {
  list-style: none;
  counter-reset: step-counter;
  padding-left: 0;
}

.method-steps li {
  counter-increment: step-counter;
  margin-bottom: 1rem;
  padding-left: 3rem;
  position: relative;
  font-size: 1.05rem;
  font-weight: 300;
  color: var(--color-text-secondary);
}

.method-steps li::before {
  content: counter(step-counter);
  position: absolute;
  left: 0;
  top: 0;
  background: var(--color-text);
  color: var(--color-background);
  width: 1.8rem;
  height: 1.8rem;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 400;
  font-size: 0.9rem;
}

.method-quote {
  margin-top: 2rem;
  padding-top: 2rem;
  border-top: 1px solid var(--color-border);
  font-style: italic;
  font-size: 1.1rem;
  color: var(--color-text);
  text-align: center;
  font-weight: 300;
}

/* Problem to Method Section */
.problem-method-section .next-section-btn {
  bottom: 1rem;
}

.method-flow {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  max-width: 900px;
  margin: 0 auto 4rem;
  align-items: center;
}

.method-step {
  background: var(--color-background-alt);
  padding: 2.5rem;
  border-radius: 12px;
  border: 2px solid var(--color-border);
  width: 100%;
  max-width: 800px;
  text-align: center;
  transition: all 0.3s ease;
  position: relative;
}

.method-step:hover {
  border-color: var(--color-text);
  transform: translateY(-5px);
}

.method-step.highlighted {
  border-color: var(--color-text);
  background: var(--color-background-alt);
}

.step-number {
  position: absolute;
  top: -20px;
  left: 50%;
  transform: translateX(-50%);
  width: 40px;
  height: 40px;
  background: var(--color-text);
  color: var(--color-background);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.2rem;
  font-weight: 600;
  font-family: 'Oswald', sans-serif;
}

.step-title {
  font-family: 'Oswald', sans-serif;
  color: var(--color-text);
  margin-bottom: 1.5rem;
  font-size: 1.5rem;
  font-weight: 400;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-top: 1rem;
}

.step-list {
  list-style: none;
  padding-left: 0;
  text-align: left;
  max-width: 600px;
  margin: 0 auto;
}

.step-list li {
  padding: 0.8rem 0 0.8rem 2rem;
  position: relative;
  font-size: 1.05rem;
  line-height: 1.6;
  font-weight: 300;
  color: var(--color-text-secondary);
}

.step-list li::before {
  content: "→";
  position: absolute;
  left: 0;
  color: var(--color-text);
  font-weight: 700;
  font-size: 1.2rem;
}

.step-note {
  margin-top: 1.5rem;
  padding-top: 1.5rem;
  border-top: 1px solid var(--color-border);
  font-style: italic;
  color: var(--color-text-muted);
  font-weight: 300;
  font-size: 0.95rem;
  text-align: center;
}

.flow-arrow {
  font-size: 2rem;
  color: var(--color-text);
  margin: 0.5rem 0;
  animation: bounce-arrow 2s infinite;
}

@keyframes bounce-arrow {
  0%, 20%, 50%, 80%, 100% {
    transform: translateY(0);
  }
  40% {
    transform: translateY(-10px);
  }
  60% {
    transform: translateY(-5px);
  }
}

/* Proactivity Section */
.proactivity-section {
  background: var(--color-background);
  color: var(--color-text-primary);
}

.proactivity-section .section-title {
  color: var(--color-text-primary);
}

.proactivity-content {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  margin-bottom: 3rem;
  max-width: 1000px;
  margin-left: auto;
  margin-right: auto;
}

.proactivity-item {
  background: var(--color-background-alt);
  border: 1px solid var(--color-border);
  padding: 2rem;
  border-radius: 12px;
  text-align: center;
  transition: all 0.3s ease;
}

.proactivity-item:hover {
  border-color: var(--color-text);
}

.icon {
  font-size: 3rem;
  display: block;
  margin-bottom: 1rem;
}

.proactivity-item p {
  font-size: 1.05rem;
  line-height: 1.6;
  font-weight: 300;
  color: var(--color-text-secondary);
}

.final-message {
  background: var(--color-background-alt);
  color: var(--color-text-primary);
  padding: 3rem;
  border-radius: 12px;
  border: 2px solid var(--color-text);
  text-align: center;
  max-width: 900px;
  margin-left: auto;
  margin-right: auto;
}

.final-message h3 {
  font-size: 1.8rem;
  margin: 0;
  line-height: 1.6;
  font-weight: 400;
  color: var(--color-text);
}

/* Footer */
.footer {
  background: var(--color-background-alt);
  color: var(--color-text-primary);
  padding: 3rem 2rem;
  text-align: center;
  border-top: 1px solid var(--color-border);
}

.footer p {
  margin: 0.5rem 0;
  font-weight: 300;
}

.instagram-link a {
  color: var(--color-text);
  text-decoration: none;
  font-weight: 400;
  transition: color 0.3s ease;
}

.instagram-link a:hover {
  color: var(--color-text-primary);
}

/* Navigation Buttons */
.next-section-btn {
  background: transparent;
  color: var(--color-text);
  border: 2px solid var(--color-text);
  padding: 0.5rem;
  font-size: 2rem;
  font-weight: 300;
  border-radius: 50%;
  cursor: pointer;
  transition: all 0.3s ease;
  margin-top: auto;
  margin-bottom: 2rem;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-left: auto;
  margin-right: auto;
  width: 3.5rem;
  height: 3.5rem;
  animation: bounce-soft 2s infinite;
  position: absolute;
  bottom: 2rem;
  left: 50%;
  transform: translateX(-50%);
}

.next-section-btn:hover {
  background: var(--color-text);
  color: var(--color-background);
  transform: translateX(-50%) translateY(3px);
}

@keyframes bounce-soft {
  0%, 20%, 50%, 80%, 100% {
    transform: translateY(0);
  }
  40% {
    transform: translateY(-10px);
  }
  60% {
    transform: translateY(-5px);
  }
}

/* Back to Top Button */
.back-to-top {
  position: fixed;
  bottom: 2rem;
  right: 2rem;
  width: 3rem;
  height: 3rem;
  background: var(--color-text);
  color: var(--color-background);
  border: none;
  border-radius: 8px;
  font-size: 1.5rem;
  cursor: pointer;
  transition: all 0.3s ease;
  z-index: 1000;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
}

.back-to-top:hover {
  background: var(--color-text-primary);
  color: var(--color-text);
  transform: translateY(-3px);
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.4);
}

/* Fade Transition */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

/* Responsive */
@media (max-width: 768px) {
  .hero-title {
    font-size: 2.5rem;
    padding: 0 1rem;
  }

  .hero-subtitle {
    font-size: 1.2rem;
    padding: 0 1rem;
  }

  .section-title {
    font-size: 2rem;
    padding: 0 0.5rem;
  }

  .section {
    padding: 3rem 1rem;
    min-height: 100vh;
  }

  .container {
    padding: 0 0.5rem;
  }

  .next-section-btn {
    bottom: 1rem;
  }

  .methodology-grid,
  .proactivity-content {
    grid-template-columns: 1fr;
  }

  .problem-flow {
    flex-direction: column;
  }

  .method-box,
  .principles,
  .quote,
  .problem-flow,
  .highlight-box,
  .final-message {
    padding: 1.5rem;
  }

  .method-step {
    padding: 2rem 1.5rem;
  }

  .step-list {
    max-width: 100%;
  }

  .step-title {
    font-size: 1.3rem;
  }

  .back-to-top {
    bottom: 1rem;
    right: 1rem;
    width: 2.5rem;
    height: 2.5rem;
    font-size: 1.2rem;
  }

  .next-section-btn {
    width: 3rem;
    height: 3rem;
    font-size: 1.5rem;
  }

  .hero-image {
    max-width: 300px;
  }

  .section-image {
    max-width: 100%;
    padding: 1rem;
  }

  .section-image-left,
  .section-image-right {
    position: relative;
    left: 0;
    right: 0;
    top: auto;
    bottom: auto;
    height: auto;
    transform: none;
    max-width: 100%;
    width: 100%;
    margin: 0 0 2rem 0;
    opacity: 0.5;
  }

  .section-image-right img {
    height: auto;
    width: 100%;
  }

  .creativity-section .container {
    margin-left: auto;
    margin-right: auto;
    max-width: 100%;
    padding-top: 0;
  }

  .creativity-section .section-title {
    text-align: center;
    max-width: 100%;
    margin-left: auto;
    margin-right: auto;
  }

  .quote,
  .question-box {
    max-width: 100%;
    margin-left: auto;
    margin-right: auto;
    text-align: center;
  }

  .quote {
    border-right: none;
    border-left: 3px solid var(--color-text);
  }
}
</style>
