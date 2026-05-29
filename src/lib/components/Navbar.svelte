<script lang="ts">
  import { base } from '$app/paths';
  import { goto } from '$app/navigation';
  import { page } from '$app/stores';
  import logoAei from '$lib/assets/logo-aei.png';

  let query = $state('');

  function handleSearch(e: Event) {
    e.preventDefault();
    if (query.trim()) goto(`${base}/cursos?q=${encodeURIComponent(query.trim())}`);
  }
</script>

<nav>
  <div class="nav-inner">
    <a href="{base}/" class="nav-brand">
      <img src={logoAei} alt="AEI" class="nav-logo" />
    </a>

    <form class="search-form" onsubmit={handleSearch}>
      <svg class="search-icon" xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><circle cx="11" cy="11" r="8"/><path d="m21 21-4.3-4.3"/></svg>
      <input
        type="text"
        placeholder="¿Qué quieres aprender?"
        bind:value={query}
        class="search-input"
      />
    </form>

    <div class="nav-links">
      <a href="{base}/#microcursos">Microcursos</a>
      <a href="{base}/#trilogia">Trilogía</a>
    </div>
    <div class="nav-actions">
      <a href="{base}/galeria" class="nav-cta secondary">Galería</a>
    </div>
  </div>
</nav>

<style>
  nav {
    position: sticky;
    top: 0;
    z-index: 100;
    background: rgba(46, 91, 168, 0.97);
    backdrop-filter: blur(8px);
  }
  .nav-inner {
    max-width: 1200px;
    margin: 0 auto;
    padding: 12px 32px;
    display: flex;
    align-items: center;
    gap: 24px;
  }
  .nav-brand { display: flex; align-items: center; flex-shrink: 0; }
  .nav-logo { height: 40px; width: 40px; border-radius: 50%; object-fit: cover; display: block; }

  .search-form {
    display: flex;
    align-items: center;
    background: white;
    border-radius: 8px;
    padding: 0 14px;
    gap: 8px;
    width: 280px;
    height: 38px;
    flex-shrink: 0;
  }
  .search-icon { color: #44546A; opacity: 0.5; flex-shrink: 0; }
  .search-input {
    flex: 1;
    border: none;
    outline: none;
    font-size: 0.875rem;
    color: #44546A;
    background: transparent;
    font-family: inherit;
  }
  .search-input::placeholder { color: rgba(68,84,106,0.45); }

  .nav-links { display: flex; gap: 20px; }
  .nav-links a { color: rgba(255,255,255,0.8); font-weight: 500; transition: color 0.2s; text-decoration: none; font-size: 0.9rem; white-space: nowrap; }
  .nav-links a:hover { color: white; }
  .nav-actions { display: flex; align-items: center; gap: 12px; flex-shrink: 0; margin-left: auto; }
  .nav-cta {
    background: #FFC000;
    color: #44546A;
    padding: 8px 18px;
    border-radius: 8px;
    font-weight: 700;
    font-size: 0.875rem;
    text-decoration: none;
    white-space: nowrap;
  }
  .nav-cta.secondary {
    background: transparent;
    color: #FFC000;
    border: 2px solid #FFC000;
  }
  .nav-cta.secondary:hover { background: rgba(255,192,0,0.1); }

  @media (max-width: 900px) {
    .nav-links { display: none; }
  }
  @media (max-width: 768px) {
    .nav-inner { padding: 12px 20px; gap: 12px; }
    .nav-login { display: none; }
    .search-form { max-width: 100%; }
  }
</style>
