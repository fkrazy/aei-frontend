<script lang="ts">
  import { base } from '$app/paths';
  import { page } from '$app/stores';
  import Navbar from '$lib/components/Navbar.svelte';
  import logoCanal from '$lib/assets/logo-canal-x-y-yo.png';

  const categorias = ['Todos', 'Radiología', 'Ultrasonido', 'Tomografía', 'Resonancia', 'Pedagogía', 'IA'];

  const cursos = [
    { id: 'radiologia-basica',       titulo: 'Radiología Básica',        categoria: 'Radiología',  precio: 99  },
    { id: 'ultrasonido-avanzado',    titulo: 'Ultrasonido Avanzado',     categoria: 'Ultrasonido', precio: 120 },
    { id: 'tomografia-computada',    titulo: 'Tomografía Computada',     categoria: 'Tomografía',  precio: 110 },
    { id: 'resonancia-magnetica',    titulo: 'Resonancia Magnética',     categoria: 'Resonancia',  precio: 130 },
    { id: 'pedagogia-digital',       titulo: 'Pedagogía Digital',        categoria: 'Pedagogía',   precio: 89  },
    { id: 'ia-diagnostico-medico',   titulo: 'IA en Diagnóstico Médico', categoria: 'IA',          precio: 149 },
  ];

  const queryCategoria = $derived($page.url.searchParams.get('categoria') ?? 'Todos');
  let categoriaActiva = $state(queryCategoria);

  const cursosFiltrados = $derived(
    categoriaActiva === 'Todos'
      ? cursos
      : cursos.filter(c => c.categoria === categoriaActiva)
  );
</script>

<svelte:head>
  <title>Catálogo de Microcursos — AEI</title>
  <meta name="description" content="Microcursos médicos de Radiología, Ultrasonido, Tomografía, Resonancia, Pedagogía e IA. Aprende con Canal X y Yo." />
</svelte:head>

<div class="page">
  <Navbar />

  <div class="hero">
    <div class="hero-inner">
      <div class="logo-glow">
        <img src={logoCanal} alt="Canal X y Yo" class="logo-img" />
      </div>
      <div class="hero-text">
        <h1>Microcursos <span class="gold">Médicos</span></h1>
        <p>Formación especializada en diagnóstico por imagen. Aprende con los mejores profesionales de Canal X y Yo.</p>
      </div>
    </div>
  </div>

  <div class="catalogo">
    <div class="container">
      <div class="filtros">
        {#each categorias as cat}
          <button
            class="filtro-btn"
            class:active={categoriaActiva === cat}
            onclick={() => categoriaActiva = cat}
          >
            {cat}
          </button>
        {/each}
      </div>

      <div class="grid">
        {#each cursosFiltrados as curso}
          <a href="{base}/cursos/{curso.id}" class="card">
            <div class="card-thumb">
              <img src={logoCanal} alt={curso.titulo} class="thumb-img" />
              <span class="badge">{curso.categoria}</span>
            </div>
            <div class="card-body">
              <h3>{curso.titulo}</h3>
              <p class="instructor">Canal X y Yo</p>
              <div class="card-footer">
                <span class="precio">${curso.precio} USD</span>
                <span class="cta">Ver más →</span>
              </div>
            </div>
          </a>
        {/each}
      </div>
    </div>
  </div>
</div>

<style>
  .page { background: var(--color-primary); min-height: 100vh; color: white; font-family: var(--font-family); }

  .hero { background: var(--color-primary-dark); padding: 60px 32px; }
  .hero-inner {
    max-width: 1200px;
    margin: 0 auto;
    display: flex;
    align-items: center;
    gap: 48px;
  }
  .logo-glow { border-radius: 50%; box-shadow: 0 0 40px 20px rgba(255,255,255,0.35); flex-shrink: 0; }
  .logo-img { width: 140px; height: 140px; border-radius: 50%; object-fit: cover; display: block; }
  .hero-text h1 { font-size: 2.25rem; font-weight: 700; margin-bottom: 12px; }
  .hero-text p { color: rgba(255,255,255,0.8); font-size: 1.05rem; line-height: 1.7; max-width: 500px; }
  .gold { color: var(--color-accent-gold); }

  .catalogo { padding: 60px 32px; }
  .container { max-width: 1200px; margin: 0 auto; }

  .filtros { display: flex; flex-wrap: wrap; gap: 12px; margin-bottom: 40px; }
  .filtro-btn {
    border: 2px solid rgba(255,255,255,0.4);
    background: transparent;
    color: rgba(255,255,255,0.8);
    padding: 8px 20px;
    border-radius: 999px;
    font-weight: 600;
    font-size: 0.875rem;
    cursor: pointer;
    transition: all 0.2s;
  }
  .filtro-btn:hover, .filtro-btn.active {
    background: var(--color-accent-gold);
    border-color: var(--color-accent-gold);
    color: var(--color-text-dark);
  }

  .grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 24px;
  }

  .card {
    background: white;
    border-radius: 12px;
    overflow: hidden;
    text-decoration: none;
    color: var(--color-text-dark);
    box-shadow: 0 2px 8px rgba(0,0,0,0.12);
    transition: transform 0.2s, box-shadow 0.2s;
    display: flex;
    flex-direction: column;
  }
  .card:hover { transform: translateY(-4px); box-shadow: 0 8px 24px rgba(0,0,0,0.2); }

  .card-thumb { position: relative; aspect-ratio: 16/9; overflow: hidden; background: var(--color-primary-dark); display: flex; align-items: center; justify-content: center; }
  .thumb-img { width: 80px; height: 80px; border-radius: 50%; object-fit: cover; }
  .badge {
    position: absolute;
    top: 12px; left: 12px;
    background: var(--color-accent-gold);
    color: var(--color-text-dark);
    font-size: 0.7rem;
    font-weight: 700;
    padding: 3px 10px;
    border-radius: 999px;
  }

  .card-body { padding: 20px; display: flex; flex-direction: column; gap: 8px; flex: 1; }
  .card-body h3 { font-size: 1rem; font-weight: 700; color: var(--color-text-dark); }
  .instructor { font-size: 0.8rem; color: var(--color-primary); font-weight: 600; }
  .card-footer { display: flex; justify-content: space-between; align-items: center; margin-top: auto; padding-top: 12px; border-top: 1px solid #eee; }
  .precio { font-size: 1.1rem; font-weight: 700; color: var(--color-text-dark); }
  .cta { font-size: 0.875rem; font-weight: 600; color: var(--color-primary); }

  @media (max-width: 900px) { .grid { grid-template-columns: repeat(2, 1fr); } }
  @media (max-width: 768px) {
    .hero { padding: 40px 20px; }
    .hero-inner { flex-direction: column; gap: 24px; text-align: center; }
    .hero-text p { max-width: 100%; }
    .catalogo { padding: 40px 20px; }
  }
  @media (max-width: 480px) { .grid { grid-template-columns: 1fr; } }
</style>
