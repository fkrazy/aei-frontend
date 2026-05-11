<script lang="ts">
  import { base } from '$app/paths';
</script>

<!-- PROPUESTA B: Recomendación experta — AEI como protagonista, layout moderno -->
<div class="page">

  <!-- NAV -->
  <nav>
    <div class="nav-inner">
      <div class="nav-brand">
        <span class="brand-aei">AEI</span>
        <span class="brand-sub">Arte Educación Inteligente</span>
      </div>
      <div class="nav-links">
        <a href="#microcursos">Microcursos</a>
        <a href="#trilogia">Trilogía</a>
        <a href="#nosotros">Nosotros</a>
      </div>
      <a href="#cursos" class="nav-cta">Comenzar ahora</a>
    </div>
  </nav>

  <!-- HERO -->
  <section class="hero">
    <div class="hero-inner">
      <div class="hero-text">
        <div class="powered-by">
          <span>Respaldado por</span>
          <strong>Canal X y Yo</strong>
        </div>
        <h1>Aprende con los mejores recursos educativos digitales</h1>
        <p>Microcursos médicos especializados y una trilogía de aprendizaje con IA para todas las edades — desde bebés hasta abuelitos.</p>
        <div class="hero-btns">
          <a href="#cursos" class="btn-primary">Explorar cursos</a>
          <a href="#trilogia" class="btn-ghost">Ver Trilogía AEI</a>
        </div>
      </div>
      <div class="hero-visual">
        <div class="logo-glow-b">
          <div class="logo-circle aei-logo">
            <span class="logo-big">AEI</span>
            <span class="logo-tagline">Arte Educación Inteligente</span>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- CATEGORÍAS -->
  <section class="categorias">
    <div class="container">
      <h2>Nuestros cursos</h2>
      <p class="subtitle">Especialidades médicas de diagnóstico por imágenes</p>
      <div class="cat-grid">
        {#each ['Radiología', 'Ultrasonido', 'Tomografía', 'Resonancia', 'Pedagogía', 'IA General'] as cat}
          <button class="cat-chip">{cat}</button>
        {/each}
      </div>
    </div>
  </section>

  <!-- CURSOS -->
  <section id="cursos" class="cursos">
    <div class="container">
      <div class="section-header">
        <h2>Microcursos disponibles</h2>
        <div class="powered-tag">
          <span>Por</span>
          <strong>Canal X y Yo</strong>
        </div>
      </div>
      <div class="cursos-grid">
        {#each [
          { titulo: 'Radiología Básica', categoria: 'Radiología', precio: '$49' },
          { titulo: 'Ultrasonido Diagnóstico', categoria: 'Ultrasonido', precio: '$59' },
          { titulo: 'Tomografía Computada', categoria: 'Tomografía', precio: '$65' },
          { titulo: 'Resonancia Magnética', categoria: 'Resonancia', precio: '$70' }
        ] as curso}
          <div class="curso-card">
            <div class="curso-thumb"></div>
            <div class="curso-body">
              <span class="curso-cat">{curso.categoria}</span>
              <h3>{curso.titulo}</h3>
              <div class="curso-footer">
                <span class="curso-precio">{curso.precio}</span>
                <button class="btn-primary small">Ver curso</button>
              </div>
            </div>
          </div>
        {/each}
      </div>
    </div>
  </section>

  <!-- TRILOGÍA -->
  <section id="trilogia" class="trilogia">
    <div class="container">
      <div class="trilogia-header">
        <div class="logo-glow-b small">
          <div class="logo-circle aei-logo small-logo">
            <span class="logo-big small-text">AEI</span>
          </div>
        </div>
        <div>
          <h2>Trilogía de Aprendizaje con <span class="highlight">Inteligencia Artificial</span></h2>
          <p>Contenido educativo adaptado a cada etapa de vida — Canción, Video y Storybook</p>
        </div>
      </div>
      <div class="edad-grid">
        {#each ['0 a 1 año', '1 a 3 años', '4 a 6 años', '7 a 10 años', '11 a 15 años', '16 a 20 años'] as rango}
          <button class="edad-card">{rango}</button>
        {/each}
      </div>
      <button class="edad-card abuelitos-card">Abuelitos</button>
    </div>
  </section>

  <!-- FOOTER -->
  <footer class="footer">
    <div class="container footer-inner">
      <div>
        <span class="brand-aei">AEI</span>
        <span class="footer-powered">Respaldado por Canal X y Yo</span>
      </div>
      <a href="{base}/" class="back">← Volver al selector</a>
    </div>
  </footer>
</div>

<style>
  .page {
    background: var(--color-bg-white);
    min-height: 100vh;
    font-family: var(--font-family);
    color: var(--color-text-dark);
  }

  .container {
    max-width: var(--spacing-container);
    margin: 0 auto;
    padding: 0 32px;
  }

  /* NAV */
  nav {
    position: sticky;
    top: 0;
    z-index: 100;
    background: white;
    border-bottom: 1px solid rgba(0,0,0,0.08);
    box-shadow: 0 2px 8px rgba(0,0,0,0.06);
  }
  .nav-inner {
    max-width: var(--spacing-container);
    margin: 0 auto;
    padding: 14px 32px;
    display: flex;
    align-items: center;
    gap: 32px;
  }
  .nav-brand { display: flex; align-items: baseline; gap: 8px; }
  .brand-aei { font-size: 1.5rem; font-weight: 700; color: var(--color-primary); }
  .brand-sub { font-size: 0.75rem; color: #999; }
  .nav-links { display: flex; gap: 24px; flex: 1; }
  .nav-links a { color: var(--color-text-dark); font-weight: 500; transition: color 0.2s; }
  .nav-links a:hover { color: var(--color-primary); }
  .nav-cta {
    background: var(--color-primary);
    color: white;
    padding: 8px 20px;
    border-radius: var(--radius-button);
    font-weight: 700;
    font-size: 0.875rem;
    transition: background 0.2s;
  }
  .nav-cta:hover { background: var(--color-primary-dark); }

  /* HERO */
  .hero {
    background: var(--color-primary);
    padding: 80px 32px;
    color: white;
  }
  .hero-inner {
    max-width: var(--spacing-container);
    margin: 0 auto;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 64px;
    align-items: center;
  }
  .powered-by {
    display: flex;
    align-items: center;
    gap: 8px;
    font-size: 0.85rem;
    color: rgba(255,255,255,0.65);
    margin-bottom: 16px;
  }
  .powered-by strong { color: var(--color-accent-gold); }
  .hero-text h1 {
    font-size: 2.5rem;
    font-weight: 700;
    line-height: 1.2;
    margin-bottom: 20px;
    color: white;
  }
  .hero-text p {
    color: rgba(255,255,255,0.75);
    font-size: 1.05rem;
    line-height: 1.7;
    margin-bottom: 32px;
  }
  .hero-btns { display: flex; gap: 16px; flex-wrap: wrap; }

  .btn-primary {
    background: var(--color-accent-gold);
    color: var(--color-text-dark);
    padding: 12px 28px;
    border-radius: var(--radius-button);
    font-weight: 700;
    font-size: 0.95rem;
    border: none;
    cursor: pointer;
    transition: opacity 0.2s;
    text-decoration: none;
    display: inline-block;
  }
  .btn-primary:hover { opacity: 0.9; }
  .btn-primary.small { padding: 7px 16px; font-size: 0.8rem; }

  .btn-ghost {
    border: 2px solid rgba(255,255,255,0.5);
    background: transparent;
    color: white;
    padding: 12px 28px;
    border-radius: var(--radius-button);
    font-weight: 600;
    font-size: 0.95rem;
    cursor: pointer;
    transition: border-color 0.2s;
    text-decoration: none;
    display: inline-block;
  }
  .btn-ghost:hover { border-color: white; }

  .hero-visual { display: flex; justify-content: center; }
  .logo-glow-b {
    border-radius: 50%;
    box-shadow: 0 0 60px 20px rgba(255,255,255,0.2);
  }
  .logo-glow-b.small { box-shadow: 0 0 30px 10px rgba(68,114,196,0.3); }
  .logo-circle {
    width: 260px;
    height: 260px;
    border-radius: 50%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 8px;
  }
  .aei-logo {
    background: linear-gradient(135deg, #1a2a5e, #2E5BA8);
    border: 3px solid rgba(255,255,255,0.3);
  }
  .logo-circle.small-logo { width: 100px; height: 100px; }
  .logo-big { font-size: 3.5rem; font-weight: 700; color: white; }
  .logo-big.small-text { font-size: 1.8rem; }
  .logo-tagline { font-size: 0.75rem; color: rgba(255,255,255,0.65); text-align: center; }

  /* CATEGORÍAS */
  .categorias {
    padding: 48px 0;
    background: var(--color-bg-light);
    border-bottom: 1px solid #e5e7eb;
  }
  .categorias h2 {
    font-size: 1.5rem;
    font-weight: 700;
    margin-bottom: 4px;
  }
  .subtitle { color: #888; font-size: 0.95rem; margin-bottom: 24px; }
  .cat-grid { display: flex; flex-wrap: wrap; gap: 12px; }
  .cat-chip {
    background: white;
    border: 2px solid var(--color-primary);
    color: var(--color-primary);
    padding: 8px 20px;
    border-radius: var(--radius-pill);
    font-weight: 600;
    font-size: 0.875rem;
    cursor: pointer;
    transition: background 0.2s, color 0.2s;
  }
  .cat-chip:hover { background: var(--color-primary); color: white; }

  /* CURSOS */
  .cursos { padding: 80px 0; }
  .section-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 36px;
  }
  .section-header h2 { font-size: 1.75rem; font-weight: 700; }
  .powered-tag {
    display: flex;
    align-items: center;
    gap: 6px;
    font-size: 0.85rem;
    color: #888;
  }
  .powered-tag strong { color: var(--color-primary); }
  .cursos-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: var(--gap-grid);
  }
  .curso-card {
    background: white;
    border-radius: var(--radius-card);
    box-shadow: var(--shadow-card);
    overflow: hidden;
    transition: transform 0.2s, box-shadow 0.2s;
  }
  .curso-card:hover { transform: translateY(-4px); box-shadow: 0 8px 24px rgba(0,0,0,0.12); }
  .curso-thumb {
    height: 140px;
    background: linear-gradient(135deg, var(--color-primary), var(--color-primary-light));
  }
  .curso-body { padding: 16px; display: flex; flex-direction: column; gap: 8px; }
  .curso-cat {
    font-size: 0.7rem;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.08em;
    color: var(--color-primary);
    background: #EEF3FB;
    padding: 2px 8px;
    border-radius: 4px;
    width: fit-content;
  }
  .curso-body h3 { font-size: 0.95rem; font-weight: 700; color: var(--color-text-dark); line-height: 1.3; }
  .curso-footer { display: flex; align-items: center; justify-content: space-between; margin-top: 8px; }
  .curso-precio { font-weight: 700; color: var(--color-primary); font-size: 1.1rem; }

  /* TRILOGÍA */
  .trilogia {
    background: var(--color-primary);
    padding: 80px 0;
    color: white;
  }
  .trilogia-header {
    display: flex;
    align-items: center;
    gap: 32px;
    margin-bottom: 48px;
  }
  .trilogia-header h2 { font-size: 1.75rem; font-weight: 700; }
  .trilogia-header p { color: rgba(255,255,255,0.7); margin-top: 8px; }
  .highlight { color: var(--color-accent-gold); }
  .edad-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 16px;
    margin-bottom: 16px;
  }
  .edad-card {
    border: 2px solid rgba(255,255,255,0.5);
    background: rgba(255,255,255,0.08);
    color: white;
    padding: 16px;
    border-radius: var(--radius-button);
    font-weight: 600;
    font-size: 1rem;
    cursor: pointer;
    transition: background 0.2s, border-color 0.2s;
    text-align: center;
  }
  .edad-card:hover { background: rgba(255,255,255,0.18); border-color: white; }
  .abuelitos-card {
    width: 100%;
    color: var(--color-accent-gold);
    border-color: var(--color-accent-gold);
  }
  .abuelitos-card:hover { background: rgba(255,192,0,0.12); }

  /* FOOTER */
  .footer {
    background: var(--color-text-dark);
    padding: 32px 0;
    color: rgba(255,255,255,0.5);
  }
  .footer-inner {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .footer-inner > div { display: flex; flex-direction: column; gap: 4px; }
  .footer-powered { font-size: 0.8rem; }
  .back { color: var(--color-accent-gold); font-weight: 600; }

  @media (max-width: 1024px) {
    .cursos-grid { grid-template-columns: repeat(2, 1fr); }
    .edad-grid { grid-template-columns: repeat(2, 1fr); }
  }
  @media (max-width: 768px) {
    .hero-inner { grid-template-columns: 1fr; }
    .hero-visual { display: none; }
    .cursos-grid { grid-template-columns: 1fr; }
    .trilogia-header { flex-direction: column; }
  }
</style>
