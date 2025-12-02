<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

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
        <h1 class="hero-title">¿resolución de problemas?</h1>
        <p class="hero-subtitle">metodología para la supervivencia</p>
        <button class="cta-button" @click="scrollToSection('intro')">
          Explorar metodología
        </button>
      </div>
      <div class="scroll-indicator">
        <span>↓</span>
      </div>
    </section>

    <!-- Introduction Section -->
    <section id="intro" class="section intro-section">
      <div class="container">
        <h2 class="section-title">¿Cómo enfrentamos los problemas?</h2>
        <div class="problem-flow">
          <div class="flow-item">
            <span class="flow-emoji">🤐</span>
            <p>Tengo un problema → no lo digo → se enquista</p>
            <small>(Miedo, indecisión, parálisis analítica, cultura del silencio)</small>
          </div>
          <div class="flow-separator">o</div>
          <div class="flow-item">
            <span class="flow-emoji">💬</span>
            <p>Lo digo → pero solo verbalizo el problema, no inicio la resolución</p>
          </div>
        </div>
        <div class="highlight-box">
          <h3>Lo que falta es método</h3>
          <p>Es necesario transformar lo difuso en proceso para poder enfocarnos en llegar a la solución</p>
          <div class="question">
            ¿Qué es más frecuente en el equipo: no decir el problema o decirlo sin avanzar?
          </div>
        </div>
        <button class="next-section-btn" @click="scrollToNextSection('intro')" aria-label="Siguiente sección">
          ↓
        </button>
      </div>
    </section>

    <!-- Methodology Section -->
    <section id="methodology" class="section methodology-section">
      <div class="container">
        <h2 class="section-title">Enfoque → Metodología de diseño</h2>
        <div class="methodology-grid">
          <div class="methodology-card">
            <h3>Diseñar objetos decorativos</h3>
            <span class="arrow">→</span>
            <h3>Diseñar objetos para problemas reales</h3>
          </div>
          <div class="methodology-card">
            <h4>Metodología proyectual</h4>
            <p>Proceso estructurado</p>
          </div>
          <div class="methodology-card highlighted">
            <h4>Design Thinking</h4>
            <p>Entender el problema, generar alternativas y testear soluciones</p>
          </div>
        </div>
        <button class="next-section-btn" @click="scrollToNextSection('methodology')" aria-label="Siguiente sección">
          ↓
        </button>
      </div>
    </section>

    <!-- Creativity Section -->
    <section id="creativity" class="section creativity-section">
      <div class="container">
        <h2 class="section-title">Idea romántica de la creatividad</h2>
        <blockquote class="quote">
          "Cuando hablamos de resolver problemas, solemos pensar en intuición, experiencia o improvisación. 
          Pero Bruno Munari nos recuerda que cualquier proceso —desde diseñar un objeto hasta desarrollar software— 
          mejora cuando abandonamos la idea romántica del 'genio' y adoptamos un método claro..."
        </blockquote>
        <div class="question-box">
          <p class="italic">¿Creatividad es solo arte?</p>
        </div>
        <button class="next-section-btn" @click="scrollToNextSection('creativity')" aria-label="Siguiente sección">
          ↓
        </button>
      </div>
    </section>

    <!-- Munari Applied Section -->
    <section id="munari" class="section munari-section">
      <div class="container">
        <h2 class="section-title">Munari aplicado al software</h2>
        <div class="principles">
          <div class="principle-item">
            <span class="bullet">•</span>
            <div>
              <strong>Desromantizar la creatividad:</strong> No esperamos genios. Esperamos procesos reproducibles.
            </div>
          </div>
          <div class="principle-item">
            <span class="bullet">•</span>
            <div>
              <strong>El diseño es una forma ordenada de resolver problemas:</strong> Igual que escribir un feature, refactorizar, o corregir un bug.
            </div>
          </div>
        </div>
        
        <div class="method-box">
          <h3>Método básico de Munari (ultra resumido):</h3>
          <ol class="method-steps">
            <li>Definir el problema</li>
            <li>Analizar contexto</li>
            <li>Generar opciones → Trasladar la duda/necesidad</li>
            <li>Prototipar</li>
            <li>Evaluar</li>
            <li>Seleccionar la solución más simple y eficaz</li>
          </ol>
          <p class="method-quote">"El método como antídoto al drama del problema."</p>
        </div>
        <button class="next-section-btn" @click="scrollToNextSection('munari')" aria-label="Siguiente sección">
          ↓
        </button>
      </div>
    </section>

    <!-- From Problem to Method Section -->
    <section id="problem-method" class="section problem-method-section">
      <div class="container">
        <h2 class="section-title">"De problema a método"</h2>
        
        <div class="examples-box">
          <h3>Ejemplos:</h3>
          <ul class="examples-list">
            <li>"No entiendo bien los criterios de aceptación de mi tarea."</li>
            <li>"Hay fricción entre dos equipos."</li>
            <li>"No tengo claridad en prioridades."</li>
          </ul>
        </div>

        <div class="redefine-box">
          <h3>Redefinir los problemas:</h3>
          <ul class="redefine-list">
            <li>¿Cuál es realmente el problema?</li>
            <li>¿Qué condiciones lo rodean?</li>
            <li>¿Qué parte es ambigua?</li>
            <li>¿Qué sería una definición clara, concreta, neutral del problema?</li>
          </ul>
        </div>

        <div class="generate-box">
          <h3>Generar caminos posibles:</h3>
          <ul class="generate-list">
            <li><em>No soluciones completas.</em></li>
            <li><em>Solo alternativas.</em></li>
            <li><em>Opciones que derivan en opciones.</em></li>
          </ul>
          <p class="note">Munari insistía en que la creatividad surge cuando existe variedad, no cuando buscamos la "respuesta perfecta" a la primera.</p>
        </div>
        <button class="next-section-btn" @click="scrollToNextSection('problem-method')" aria-label="Siguiente sección">
          ↓
        </button>
      </div>
    </section>

    <!-- Proactivity Section -->
    <section id="proactivity" class="section proactivity-section">
      <div class="container">
        <h2 class="section-title">Proactividad ≠ espontaneidad</h2>
        <div class="proactivity-content">
          <div class="proactivity-item">
            <span class="icon">🎯</span>
            <p>La iniciativa no es actuar sin pensar, sino iniciar un proceso consciente.</p>
          </div>
          <div class="proactivity-item">
            <span class="icon">💻</span>
            <p>En tecnología, donde los problemas son constantes, el diseño como método es una herramienta extremadamente poderosa.</p>
          </div>
          <div class="proactivity-item">
            <span class="icon">🔄</span>
            <p>Un problema empieza a resolverse cuando deja de ser un drama y se convierte en un proceso.</p>
          </div>
        </div>
        
        <div class="final-message">
          <h3>No se buscan héroes que resuelvan problemas, sino equipos que sepan diseñar soluciones.</h3>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
      <div class="container">
        <p>Metodología para la resolución de problemas</p>
        <p class="instagram-link">
          <a href="https://www.instagram.com/reel/DQnyCTXDgXG/?igsh=Z3NwdWZ2cm92azhq" target="_blank" rel="noopener noreferrer">
            Ver más en Instagram →
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
        aria-label="Volver arriba"
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

.hero.fade-in {
  opacity: 1;
  transform: translateY(0);
}

.hero-title {
  font-size: 4rem;
  font-weight: 300;
  margin: 0;
  text-align: center;
  line-height: 1.2;
  margin-bottom: 1rem;
  letter-spacing: -0.02em;
}

.hero-subtitle {
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
  min-height: 70vh;
  display: flex;
  align-items: center;
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
}

.section-title {
  font-size: 2.5rem;
  font-weight: 300;
  margin-bottom: 3rem;
  text-align: center;
  color: var(--color-text-primary);
  letter-spacing: -0.02em;
}

/* Introduction Section */
.problem-flow {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  margin-bottom: 3rem;
  max-width: 900px;
  margin-left: auto;
  margin-right: auto;
}

.flow-item {
  background: var(--color-background-alt);
  padding: 2rem;
  border-radius: 12px;
  border: 1px solid var(--color-border);
  transition: all 0.3s ease;
  text-align: left;
}

.flow-item:hover {
  border-color: var(--color-text);
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
}

.flow-separator {
  text-align: center;
  font-size: 1.2rem;
  font-weight: 300;
  color: var(--color-text-muted);
}

.highlight-box {
  background: var(--color-background-alt);
  color: var(--color-text-primary);
  padding: 3rem;
  border-radius: 12px;
  text-align: center;
  max-width: 900px;
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
.methodology-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  max-width: 1000px;
  margin: 0 auto;
}

.methodology-card {
  background: var(--color-background-alt);
  padding: 2.5rem;
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
  display: block;
  margin: 1rem 0;
  color: var(--color-text);
  font-weight: 300;
}

/* Creativity Section */
.creativity-section {
  background: var(--color-background);
  color: var(--color-text-primary);
}

.creativity-section .section-title {
  color: var(--color-text-primary);
}

.quote {
  font-size: 1.2rem;
  line-height: 1.8;
  font-style: italic;
  padding: 2rem;
  background: transparent;
  border-left: 3px solid var(--color-text);
  border-radius: 8px;
  margin-bottom: 2rem;
  max-width: 900px;
  margin-left: auto;
  margin-right: auto;
  text-align: left;
  font-weight: 300;
  color: var(--color-text-secondary);
}

.question-box {
  text-align: center;
  font-size: 1.3rem;
  margin-top: 2rem;
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
  text-align: left;
  max-width: 900px;
  margin-left: auto;
  margin-right: auto;
}

.principle-item {
  display: flex;
  gap: 1rem;
  margin-bottom: 1.5rem;
  font-size: 1.05rem;
  line-height: 1.7;
  font-weight: 300;
  color: var(--color-text-secondary);
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
.examples-box,
.redefine-box,
.generate-box {
  background: var(--color-background-alt);
  padding: 2.5rem;
  border-radius: 12px;
  border: 1px solid var(--color-border);
  margin-bottom: 2rem;
  max-width: 900px;
  margin-left: auto;
  margin-right: auto;
  text-align: left;
}

.examples-box h3,
.redefine-box h3,
.generate-box h3 {
  color: var(--color-text);
  margin-bottom: 1.5rem;
  font-size: 1.3rem;
  font-weight: 400;
}

.examples-list,
.redefine-list,
.generate-list {
  list-style: none;
  padding-left: 0;
}

.examples-list li,
.redefine-list li,
.generate-list li {
  padding: 0.8rem 0 0.8rem 2rem;
  position: relative;
  font-size: 1.05rem;
  line-height: 1.6;
  font-weight: 300;
  color: var(--color-text-secondary);
}

.examples-list li::before {
  content: "💭";
  position: absolute;
  left: 0;
}

.redefine-list li::before {
  content: "❓";
  position: absolute;
  left: 0;
}

.generate-list li::before {
  content: "→";
  position: absolute;
  left: 0;
  color: var(--color-text);
  font-weight: 700;
}

.note {
  margin-top: 1.5rem;
  padding-top: 1.5rem;
  border-top: 1px solid var(--color-border);
  font-style: italic;
  color: var(--color-text-muted);
  font-weight: 300;
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
  margin-top: 3rem;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-left: auto;
  margin-right: auto;
  width: 3.5rem;
  height: 3.5rem;
  animation: bounce-soft 2s infinite;
}

.next-section-btn:hover {
  background: var(--color-text);
  color: var(--color-background);
  transform: translateY(3px);
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
  }

  .container {
    padding: 0 0.5rem;
  }

  .methodology-grid,
  .proactivity-content {
    grid-template-columns: 1fr;
  }

  .method-box,
  .examples-box,
  .redefine-box,
  .generate-box,
  .principles,
  .quote,
  .problem-flow,
  .highlight-box,
  .final-message {
    padding: 1.5rem;
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
}
</style>
