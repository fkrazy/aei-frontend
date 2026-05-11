<script lang="ts">
  import { base } from '$app/paths';
  const cursos = ['Radiología Básica', 'Ultrasonido Avanzado', 'Tomografía Computada', 'Resonancia Magnética'];
</script>

<!-- PROPUESTA A: Fiel al cliente — fondo azul dominante -->
<div class="page">

  <!-- NAV -->
  <nav>
    <div class="nav-inner">
      <div class="nav-brand">AEI</div>
      <div class="nav-links">
        <a href="#microcursos">Microcursos</a>
        <a href="#trilogia">Trilogía</a>
        <a href="#nosotros">Nosotros</a>
      </div>
      <a href="#cursos" class="nav-cta">Ver cursos</a>
    </div>
  </nav>

  <!-- HERO -->
  <section class="hero">
    <div class="diagonal-top"></div>
    <div class="hero-inner">
      <div class="logo-wrap">
        <div class="logo-glow">
          <div class="logo-placeholder canal">
            <span class="logo-text">Canal X y Yo</span>
            <span class="logo-sub">Enseñando a producir imágenes para el diagnóstico médico</span>
          </div>
        </div>
      </div>
      <div class="hero-center">
        <h1>Arte Educación <span class="gold">Inteligente</span></h1>
        <p>Plataforma de recursos educativos digitales — aprendizaje, creatividad e inclusión</p>
        <div class="hero-btns">
          <a href="#cursos" class="btn-outline">Explorar cursos</a>
          <a href="#trilogia" class="btn-outline">Trilogía AEI</a>
        </div>
      </div>
      <div class="logo-wrap">
        <div class="logo-glow">
          <div class="logo-placeholder aei">
            <span class="logo-text">AEI</span>
            <span class="logo-sub">Arte Educación Inteligente</span>
          </div>
        </div>
      </div>
    </div>
    <div class="vision-mision">
      <div class="vm-block">
        <h3 class="vm-label">Visión</h3>
        <p>Convertirnos en una plataforma líder en la creación y venta de recursos educativos digitales, reconocida por combinar calidad pedagógica, inclusión e innovación.</p>
      </div>
      <div class="vm-block">
        <h3 class="vm-label">Misión</h3>
        <p>Crear y comercializar recursos educativos digitales que integren aprendizaje, creatividad e inclusión, ofreciendo materiales prácticos, atractivos y adaptables.</p>
      </div>
    </div>
  </section>

  <!-- MICROCURSOS -->
  <section id="microcursos" class="microcursos">
    <h2 class="section-title gold">MICROCURSOS</h2>
    <div class="hub">
      <div class="hub-left">
        <button class="age-btn">Radiología</button>
        <button class="age-btn">Tomografía</button>
        <button class="age-btn">Pedagogía</button>
      </div>
      <div class="hub-center">
        <div class="logo-glow large">
          <div class="logo-placeholder canal large">
            <span class="logo-text">Canal X y Yo</span>
          </div>
        </div>
      </div>
      <div class="hub-right">
        <button class="age-btn">Ultrasonido</button>
        <button class="age-btn">Resonancia</button>
        <button class="age-btn">IA General</button>
      </div>
    </div>
  </section>

  <!-- CURSOS LIST -->
  <section id="cursos" class="cursos-list">
    <div class="cursos-inner">
      <div class="logo-glow">
        <div class="logo-placeholder canal">
          <span class="logo-text">Canal X y Yo</span>
        </div>
      </div>
      <div class="cursos-cards">
        {#each ['Radiología Básica', 'Ultrasonido Avanzado', 'Tomografía Computada', 'Resonancia Magnética'] as curso}
          <div class="curso-row">
            <span>{curso}</span>
            <button class="btn-outline small">Ver curso</button>
          </div>
        {/each}
      </div>
    </div>
  </section>

  <!-- TRILOGÍA -->
  <section id="trilogia" class="trilogia">
    <p class="trilogia-title-box">Trilogía de Aprendizaje con Inteligencia Artificial</p>
    <div class="trilogia-inner">
      <div class="logo-glow">
        <div class="logo-placeholder aei">
          <span class="logo-text">AEI</span>
        </div>
      </div>
      <div class="edad-grid">
        {#each [['0 a 1 año', '1 a 3 años'], ['4 a 6 años', '7 a 10 años'], ['11 a 15 años', '16 a 20 años']] as fila}
          <div class="edad-fila">
            {#each fila as rango}
              <button class="age-btn">{rango}</button>
            {/each}
          </div>
        {/each}
        <button class="age-btn full abuelitos">Abuelitos</button>
      </div>
    </div>
  </section>

  <footer class="footer">
    <a href="{base}/" class="back">← Volver al selector</a>
    <span>AEI · Arte Educación Inteligente</span>
  </footer>
</div>


<style>
  .page {
    background: var(--color-primary);
    min-height: 100vh;
    color: white;
    font-family: var(--font-family);
  }

  /* NAV */
  nav {
    position: sticky;
    top: 0;
    z-index: 100;
    background: rgba(46, 91, 168, 0.95);
    backdrop-filter: blur(8px);
    border-bottom: none;
  }
  .nav-inner {
    max-width: var(--spacing-container);
    margin: 0 auto;
    padding: 16px 32px;
    display: flex;
    align-items: center;
    gap: 32px;
  }
  .nav-brand { font-size: 1.5rem; font-weight: 700; color: var(--color-accent-gold); }
  .nav-links { display: flex; gap: 24px; flex: 1; }
  .nav-links a { color: rgba(255,255,255,0.8); font-weight: 500; transition: color 0.2s; }
  .nav-links a:hover { color: white; }
  .nav-cta {
    background: var(--color-accent-gold);
    color: var(--color-text-dark);
    padding: 8px 20px;
    border-radius: var(--radius-button);
    font-weight: 700;
    font-size: 0.875rem;
  }

  /* HERO */
  .hero {
    position: relative;
    padding: 60px 32px 40px;
    overflow: hidden;
  }
  .diagonal-top {
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 60px;
    background: white;
    clip-path: polygon(0 0, 100% 0, 85% 100%, 0 100%);
    opacity: 0.15;
  }
  .hero-inner {
    max-width: var(--spacing-container);
    margin: 0 auto;
    display: grid;
    grid-template-columns: 1fr 2fr 1fr;
    gap: 32px;
    align-items: center;
  }
  .logo-wrap { display: flex; justify-content: center; }
  .logo-glow {
    border-radius: 50%;
    box-shadow: var(--shadow-glow);
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .logo-placeholder {
    width: 180px;
    height: 180px;
    border-radius: 50%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 8px;
    text-align: center;
    padding: 20px;
  }
  .logo-placeholder.canal { background: #f0f0f0; }
  .logo-placeholder.aei { background: #1a2a5e; border: 3px solid #5B9BD5; }
  .logo-placeholder.large { width: 240px; height: 240px; }
  .logo-glow.large { box-shadow: 0 0 60px 30px rgba(255,255,255,0.35); }
  .logo-text { font-weight: 700; font-size: 1.1rem; color: var(--color-text-dark); }
  .logo-placeholder.aei .logo-text { color: white; font-size: 1.8rem; }
  .logo-sub { font-size: 0.7rem; color: #666; text-align: center; line-height: 1.3; }
  .logo-placeholder.aei .logo-sub { color: rgba(255,255,255,0.7); }

  .hero-center { text-align: center; display: flex; flex-direction: column; align-items: center; gap: 20px; }
  .hero-center h1 { font-size: 2.5rem; font-weight: 700; color: white; line-height: 1.2; }
  .hero-center p { color: rgba(255,255,255,0.75); font-size: 1.1rem; max-width: 400px; }
  .hero-btns { display: flex; gap: 16px; }

  .gold { color: var(--color-accent-gold); }

  .btn-outline {
    border: 2px solid rgba(255,255,255,0.7);
    background: transparent;
    color: white;
    padding: 10px 24px;
    border-radius: var(--radius-button);
    font-weight: 600;
    font-size: 0.95rem;
    cursor: pointer;
    transition: background 0.2s, border-color 0.2s;
    text-decoration: none;
    display: inline-block;
  }
  .btn-outline:hover { background: rgba(255,255,255,0.1); border-color: white; }
  .btn-outline.small { padding: 6px 14px; font-size: 0.8rem; }

  .vision-mision {
    max-width: var(--spacing-container);
    margin: 40px auto 0;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 32px;
    padding: 0 32px;
  }
  .vm-block { display: flex; flex-direction: column; gap: 8px; }
  .vm-label { font-size: 1.5rem; font-weight: 700; color: rgba(255,255,255,0.2); }
  .vm-block p { color: rgba(255,255,255,0.8); font-size: 0.95rem; line-height: 1.7; }

  /* MICROCURSOS */
  .microcursos {
    padding: 80px 32px;
    background: var(--color-primary-dark);
  }
  .section-title {
    text-align: center;
    font-size: 2rem;
    font-weight: 700;
    margin-bottom: 48px;
    letter-spacing: 0.05em;
  }
  .hub {
    max-width: 900px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: 1fr auto 1fr;
    gap: 24px;
    align-items: center;
  }
  .hub-left, .hub-right { display: flex; flex-direction: column; gap: 16px; }
  .hub-right { align-items: flex-end; }
  .hub-center { display: flex; justify-content: center; }

  .age-btn {
    border: 2px solid rgba(255,255,255,0.6);
    background: rgba(255,255,255,0.08);
    color: white;
    padding: 12px 24px;
    border-radius: var(--radius-button);
    font-weight: 600;
    font-size: 0.95rem;
    cursor: pointer;
    transition: background 0.2s;
    min-width: 160px;
    text-align: center;
  }
  .age-btn:hover { background: rgba(255,255,255,0.18); }
  .age-btn.full { width: 100%; }
  .age-btn.abuelitos { color: var(--color-accent-gold); border-color: var(--color-accent-gold); }

  /* CURSOS LIST */
  .cursos-list { padding: 80px 32px; }
  .cursos-inner {
    max-width: var(--spacing-container);
    margin: 0 auto;
    display: grid;
    grid-template-columns: auto 1fr;
    gap: 48px;
    align-items: start;
  }
  .cursos-cards { display: flex; flex-direction: column; gap: 16px; }
  .curso-row {
    background: rgba(255,255,255,0.1);
    border: 1px solid rgba(255,255,255,0.2);
    border-radius: var(--radius-button);
    padding: 16px 24px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-weight: 600;
  }

  /* TRILOGÍA */
  .trilogia { padding: 80px 32px; background: var(--color-primary-dark); }
  .trilogia-title-box {
    display: block;
    background: white;
    color: #333;
    border: 1px solid #ccc;
    padding: 10px 24px;
    border-radius: 4px;
    font-size: 1rem;
    width: fit-content;
    margin: 0 auto 40px;
  }
  .trilogia-inner {
    max-width: 900px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: auto 1fr;
    gap: 48px;
    align-items: center;
  }
  .edad-grid { display: flex; flex-direction: column; gap: 16px; }
  .edad-fila { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; }

  /* FOOTER */
  .footer {
    padding: 32px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-top: 1px solid rgba(255,255,255,0.15);
    font-size: 0.875rem;
    color: rgba(255,255,255,0.5);
  }
  .back { color: var(--color-accent-gold); font-weight: 600; }

  @media (max-width: 768px) {
    .hero-inner { grid-template-columns: 1fr; }
    .vision-mision { grid-template-columns: 1fr; }
    .hub { grid-template-columns: 1fr; }
    .cursos-inner { grid-template-columns: 1fr; }
    .trilogia-inner { grid-template-columns: 1fr; }
  }
</style>
