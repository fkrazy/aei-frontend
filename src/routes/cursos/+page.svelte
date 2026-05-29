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
  const queryBusqueda = $derived($page.url.searchParams.get('q') ?? '');

  let categoriaActiva = $state(queryCategoria);
  let busqueda = $state(queryBusqueda);

  const cursosFiltrados = $derived(
    cursos.filter(c => {
      const matchCategoria = categoriaActiva === 'Todos' || c.categoria === categoriaActiva;
      const matchBusqueda = !busqueda || c.titulo.toLowerCase().includes(busqueda.toLowerCase());
      return matchCategoria && matchBusqueda;
    })
  );
</script>

<svelte:head>
  <title>Catálogo de Microcursos — AEI</title>
  <meta name="description" content="Microcursos médicos de Radiología, Ultrasonido, Tomografía, Resonancia, Pedagogía e IA. Aprende con Canal X y Yo." />
</svelte:head>

<div class="page">
  <Navbar />

  <div class="catalogo">
    <div class="container">

      <div class="page-header">
        <div>
          <h1>Catálogo <span class="gold">de Cursos</span></h1>
          {#if busqueda}
            <p class="resultados">Resultados para "<strong>{busqueda}</strong>" — {cursosFiltrados.length} curso{cursosFiltrados.length !== 1 ? 's' : ''}</p>
          {/if}
        </div>
        {#if busqueda}
          <button class="clear-search" onclick={() => busqueda = ''}>✕ Limpiar búsqueda</button>
        {/if}
      </div>

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

      {#if cursosFiltrados.length > 0}
        <div class="grid">
          {#each cursosFiltrados as curso}
            <a href="{base}/cursos/{curso.id}" class="card">
              <div class="card-thumb">
                <div class="thumb-bg">
                  <img src={logoCanal} alt={curso.titulo} class="thumb-logo" />
                </div>
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
      {:else}
        <div class="empty">
          <p>No se encontraron cursos para "<strong>{busqueda}</strong>".</p>
          <button class="filtro-btn active" onclick={() => { busqueda = ''; categoriaActiva = 'Todos'; }}>Ver todos los cursos</button>
        </div>
      {/if}

    </div>
  </div>
</div>

<style>
  .page { background: var(--color-primary); min-height: 100vh; color: white; font-family: var(--font-family); }

  .catalogo { padding: 48px 32px; }
  .container { max-width: 1200px; margin: 0 auto; }

  .page-header {
    display: flex;
    align-items: flex-end;
    justify-content: space-between;
    margin-bottom: 32px;
    gap: 16px;
  }
  .page-header h1 { font-size: 2rem; font-weight: 700; }
  .gold { color: var(--color-accent-gold); }
  .resultados { color: rgba(255,255,255,0.7); font-size: 0.9rem; margin-top: 6px; }
  .clear-search {
    background: none;
    border: 1px solid rgba(255,255,255,0.4);
    color: rgba(255,255,255,0.7);
    padding: 8px 16px;
    border-radius: 8px;
    font-size: 0.8rem;
    cursor: pointer;
    white-space: nowrap;
    transition: all 0.2s;
    font-family: inherit;
  }
  .clear-search:hover { color: white; border-color: white; }

  .filtros { display: flex; flex-wrap: wrap; gap: 10px; margin-bottom: 36px; }
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
    font-family: inherit;
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

  .card-thumb {
    position: relative;
    aspect-ratio: 16/9;
    background: linear-gradient(135deg, var(--color-primary-dark) 0%, var(--color-primary) 100%);
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
  }
  .thumb-bg {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 100%;
  }
  .thumb-logo {
    width: 72px;
    height: 72px;
    border-radius: 50%;
    object-fit: cover;
    box-shadow: 0 0 24px 8px rgba(255,255,255,0.2);
  }
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

  .card-body { padding: 18px 20px; display: flex; flex-direction: column; gap: 6px; flex: 1; }
  .card-body h3 { font-size: 1rem; font-weight: 700; color: var(--color-text-dark); line-height: 1.3; }
  .instructor { font-size: 0.8rem; color: var(--color-primary); font-weight: 600; }
  .card-footer { display: flex; justify-content: space-between; align-items: center; margin-top: auto; padding-top: 12px; border-top: 1px solid #eee; }
  .precio { font-size: 1.05rem; font-weight: 700; color: var(--color-text-dark); }
  .cta { font-size: 0.875rem; font-weight: 600; color: var(--color-primary); }

  .empty { text-align: center; padding: 80px 0; display: flex; flex-direction: column; align-items: center; gap: 24px; }
  .empty p { color: rgba(255,255,255,0.7); font-size: 1rem; }

  @media (max-width: 900px) { .grid { grid-template-columns: repeat(2, 1fr); } }
  @media (max-width: 768px) {
    .catalogo { padding: 32px 20px; }
    .page-header { flex-direction: column; align-items: flex-start; }
  }
  @media (max-width: 480px) { .grid { grid-template-columns: 1fr; } }
</style>
