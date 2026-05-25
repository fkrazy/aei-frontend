<script lang="ts">
  import { base } from '$app/paths';
  import logoAei from '$lib/assets/logo-aei.png';
</script>

<nav>
  <div class="nav-inner">
    <a href="{base}/" class="nav-brand">
      <img src={logoAei} alt="AEI" class="nav-logo" />
    </a>
    <div class="nav-links">
      <a href="{base}/#microcursos">Microcursos</a>
      <a href="{base}/#trilogia">Trilogía</a>
      <a href="{base}/cursos">Catálogo</a>
    </div>
    <div class="nav-actions">
      <a href="{base}/auth/login" class="nav-login">Iniciar sesión</a>
      <a href="{base}/cursos" class="nav-cta">Ver cursos</a>
    </div>
  </div>
</nav>

<style>
  nav {
    position: sticky;
    top: 0;
    z-index: 100;
    background: rgba(46, 91, 168, 0.95);
    backdrop-filter: blur(8px);
  }
  .nav-inner {
    max-width: 1200px;
    margin: 0 auto;
    padding: 16px 32px;
    display: flex;
    align-items: center;
    gap: 32px;
  }
  .nav-brand { display: flex; align-items: center; flex-shrink: 0; }
  .nav-logo { height: 44px; width: 44px; border-radius: 50%; object-fit: cover; display: block; }
  .nav-links { display: flex; gap: 24px; flex: 1; }
  .nav-links a { color: rgba(255,255,255,0.8); font-weight: 500; transition: color 0.2s; text-decoration: none; }
  .nav-links a:hover { color: white; }
  .nav-actions { display: flex; align-items: center; gap: 16px; }
  .nav-login { color: rgba(255,255,255,0.8); font-weight: 500; text-decoration: none; font-size: 0.875rem; }
  .nav-login:hover { color: white; }
  .nav-cta {
    background: #FFC000;
    color: #44546A;
    padding: 8px 20px;
    border-radius: 8px;
    font-weight: 700;
    font-size: 0.875rem;
    text-decoration: none;
    white-space: nowrap;
  }

  @media (max-width: 768px) {
    .nav-inner { padding: 14px 20px; gap: 16px; }
    .nav-links { display: none; }
    .nav-login { display: none; }
  }
</style>
