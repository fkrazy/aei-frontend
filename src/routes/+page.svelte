<script lang="ts">
  import { base } from '$app/paths';
  import logoCanal from '$lib/assets/logo-canal-x-y-yo.png';
  import logoAei from '$lib/assets/logo-aei.png';
</script>

<div class="page">

  <!-- NAV -->
  <nav>
    <div class="nav-inner">
      <a href="{base}/" class="nav-brand">
        <img src={logoAei} alt="AEI" class="nav-logo" />
      </a>
      <div class="nav-links">
        <a href="#microcursos">Microcursos</a>
        <a href="#trilogia">Trilogía</a>
        <a href="#nosotros">Nosotros</a>
      </div>
      <a href="#microcursos" class="nav-cta">Ver cursos</a>
    </div>
  </nav>

  <!-- HERO -->
  <section class="hero">
    <div class="hero-inner">
      <div class="logo-wrap">
        <div class="logo-glow">
          <img src={logoCanal} alt="Canal X y Yo" class="logo-img" />
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
          <img src={logoAei} alt="AEI — Arte Educación Inteligente" class="logo-img" />
        </div>
      </div>
    </div>
    <div class="vision-mision">
      <div class="vm-block">
        <h3 class="vm-label">Visión</h3>
        <p>Convertirnos en una plataforma líder en la creación y venta de recursos educativos digitales, reconocida por combinar calidad pedagógica, inclusión e innovación, generando soluciones de aprendizaje que aporten valor real a las personas y sostenibilidad al proyecto.</p>
      </div>
      <div class="vm-block">
        <h3 class="vm-label">Misión</h3>
        <p>Crear y comercializar recursos educativos digitales que integren aprendizaje, creatividad e inclusión, ofreciendo materiales prácticos, atractivos y adaptables para distintos públicos, con el propósito de construir una propuesta educativa rentable, escalable y con impacto positivo.</p>
      </div>
    </div>
  </section>

  <!-- MICROCURSOS -->
  <section id="microcursos" class="microcursos">
    <h2 class="section-title gold">MICROCURSOS</h2>
    <div class="hub">
      <div class="hub-left">
        <a href="{base}/cursos?categoria=Radiolog%C3%ADa" class="age-btn">Radiología</a>
        <a href="{base}/cursos?categoria=Tomograf%C3%ADa" class="age-btn">Tomografía</a>
        <a href="{base}/cursos?categoria=Pedagog%C3%ADa" class="age-btn">Pedagogía</a>
      </div>
      <div class="hub-center">
        <div class="logo-glow large">
          <img src={logoCanal} alt="Canal X y Yo" class="logo-img large" />
        </div>
      </div>
      <div class="hub-right">
        <a href="{base}/cursos?categoria=Ultrasonido" class="age-btn">Ultrasonido</a>
        <a href="{base}/cursos?categoria=Resonancia" class="age-btn">Resonancia</a>
        <a href="{base}/cursos?categoria=IA" class="age-btn">IA General</a>
      </div>
    </div>
  </section>

  <!-- TRILOGÍA -->
  <section id="trilogia" class="trilogia">
    <p class="trilogia-title-box">Trilogía de Aprendizaje con Inteligencia Artificial</p>
    <div class="trilogia-inner">
      <div class="logo-glow">
        <img src={logoAei} alt="AEI — Arte Educación Inteligente" class="logo-img" />
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
  .nav-brand { display: flex; align-items: center; flex-shrink: 0; }
  .nav-logo {
    height: 44px;
    width: 44px;
    border-radius: 50%;
    object-fit: cover;
    display: block;
  }
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
  .logo-img {
    width: 180px;
    height: 180px;
    border-radius: 50%;
    object-fit: cover;
    display: block;
  }
  .logo-img.large { width: 240px; height: 240px; }
  .logo-glow.large { box-shadow: 0 0 60px 30px rgba(255,255,255,0.35); }

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
    margin: 56px auto 0;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 40px;
    padding: 40px 32px;
    background: rgba(0,0,0,0.15);
    border-radius: 12px;
  }
  .vm-block { display: flex; flex-direction: column; gap: 12px; }
  .vm-label { font-size: 1.25rem; font-weight: 700; color: var(--color-accent-gold); text-transform: uppercase; letter-spacing: 0.08em; }
  .vm-block p { color: white; font-size: 0.95rem; line-height: 1.8; }

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
    justify-content: center;
    align-items: center;
    border-top: 1px solid rgba(255,255,255,0.15);
    font-size: 0.875rem;
    color: rgba(255,255,255,0.5);
  }

  @media (max-width: 768px) {
    /* NAV */
    .nav-inner { padding: 14px 20px; gap: 16px; }
    .nav-links { display: none; }

    /* HERO */
    .hero { padding: 40px 20px 32px; }
    .hero-inner {
      grid-template-columns: 1fr 1fr;
      grid-template-rows: auto auto;
    }
    .hero-center {
      grid-column: 1 / -1;
      order: -1;
    }
    .hero-center h1 { font-size: 1.8rem; }
    .hero-btns { flex-wrap: wrap; justify-content: center; }

    /* VISIÓN/MISIÓN */
    .vision-mision {
      grid-template-columns: 1fr;
      padding: 0 20px;
      margin-top: 32px;
    }

    /* MICROCURSOS */
    .microcursos { padding: 60px 20px; }
    .hub {
      grid-template-columns: 1fr 1fr;
      grid-template-rows: auto auto;
      gap: 16px;
    }
    .hub-center {
      grid-column: 1 / -1;
      order: -1;
    }
    .age-btn { min-width: unset; width: 100%; }

    /* TRILOGÍA */
    .trilogia { padding: 60px 20px; }
    .trilogia-title-box { font-size: 0.9rem; padding: 8px 16px; }
    .trilogia-inner { grid-template-columns: 1fr; gap: 32px; }
    .trilogia-inner .logo-glow { display: none; }
    .edad-fila { gap: 12px; }
  }

  @media (max-width: 480px) {
    .hero-inner { grid-template-columns: 1fr; }
    .logo-img { width: 140px; height: 140px; }
    .hero-center h1 { font-size: 1.5rem; }
    .hero-center p { font-size: 1rem; }
    .hub-left, .hub-right { grid-template-columns: 1fr; }
    .edad-fila { grid-template-columns: 1fr; }
  }
</style>
