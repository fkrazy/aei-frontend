<script lang="ts">
  import { base } from '$app/paths';
  import Navbar from '$lib/components/Navbar.svelte';
  import logoCanal from '$lib/assets/logo-canal-x-y-yo.png';
  import Icon from '@iconify/svelte';

  const filtros = ['Todos', 'Música', 'Videos'];
  let filtroActivo = $state('Todos');

  const items = [
    { id: 1, tipo: 'Música',  titulo: 'Canción del Cuerpo Humano',   duracion: '3:24', descripcion: 'Aprende las partes del cuerpo con esta canción educativa.' },
    { id: 2, tipo: 'Videos',  titulo: 'Introducción a la Radiología', duracion: '8:12', descripcion: 'Video introductorio sobre el mundo de la imagenología.' },
    { id: 3, tipo: 'Música',  titulo: 'El Sistema Óseo',              duracion: '2:58', descripcion: 'Canción para aprender los huesos principales del esqueleto.' },
    { id: 4, tipo: 'Videos',  titulo: 'Cómo funciona un TAC',         duracion: '6:45', descripcion: 'Explicación visual del funcionamiento de la tomografía.' },
    { id: 5, tipo: 'Música',  titulo: 'Ritmo y Anatomía',             duracion: '4:10', descripcion: 'Música educativa para memorizar conceptos de anatomía.' },
    { id: 6, tipo: 'Videos',  titulo: 'Ultrasonido en Pediatría',     duracion: '11:30', descripcion: 'Video demostrativo de ultrasonido pediátrico.' },
  ];

  const itemsFiltrados = $derived(
    filtroActivo === 'Todos' ? items : items.filter(i => i.tipo === filtroActivo)
  );
</script>

<svelte:head>
  <title>Galería — AEI</title>
  <meta name="description" content="Música y videos educativos de Canal X y Yo." />
</svelte:head>

<div class="page">
  <Navbar />

  <div class="catalogo">
    <div class="container">

      <div class="page-header">
        <h1>Galería <span class="gold">Multimedia</span></h1>
        <p class="subtitulo">Música y videos educativos de Canal X y Yo</p>
      </div>

      <div class="filtros">
        {#each filtros as f}
          <button
            class="filtro-btn"
            class:active={filtroActivo === f}
            onclick={() => filtroActivo = f}
          >{f}</button>
        {/each}
      </div>

      <div class="grid">
        {#each itemsFiltrados as item}
          <div class="card">
            <div class="card-thumb">
              <div class="thumb-bg">
                <img src={logoCanal} alt={item.titulo} class="thumb-logo" />
                <div class="play-btn">
                  <Icon icon={item.tipo === 'Música' ? 'mdi:music' : 'mdi:play-circle'} width="48" height="48" />
                </div>
              </div>
              <span class="badge">{item.tipo}</span>
              <span class="duracion">{item.duracion}</span>
            </div>
            <div class="card-body">
              <h3>{item.titulo}</h3>
              <p class="instructor">Canal X y Yo</p>
              <p class="desc">{item.descripcion}</p>
            </div>
          </div>
        {/each}
      </div>

    </div>
  </div>
</div>

<style>
  .page { background: var(--color-primary); min-height: 100vh; color: white; font-family: var(--font-family); }

  .catalogo { padding: 48px 32px; }
  .container { max-width: 1200px; margin: 0 auto; }

  .page-header { margin-bottom: 32px; }
  .page-header h1 { font-size: 2rem; font-weight: 700; }
  .gold { color: var(--color-accent-gold); }
  .subtitulo { color: rgba(255,255,255,0.65); font-size: 0.95rem; margin-top: 6px; }

  .filtros { display: flex; gap: 10px; margin-bottom: 36px; }
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

  .grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 24px; }

  .card {
    background: white;
    border-radius: 12px;
    overflow: hidden;
    color: var(--color-text-dark);
    box-shadow: 0 2px 8px rgba(0,0,0,0.12);
    transition: transform 0.2s, box-shadow 0.2s;
    cursor: pointer;
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
  .thumb-bg { position: relative; display: flex; align-items: center; justify-content: center; width: 100%; height: 100%; }
  .thumb-logo { width: 64px; height: 64px; border-radius: 50%; object-fit: cover; opacity: 0.4; }
  .play-btn { position: absolute; color: white; opacity: 0.9; }
  .badge {
    position: absolute; top: 12px; left: 12px;
    background: var(--color-accent-gold); color: var(--color-text-dark);
    font-size: 0.7rem; font-weight: 700; padding: 3px 10px; border-radius: 999px;
  }
  .duracion {
    position: absolute; bottom: 10px; right: 10px;
    background: rgba(0,0,0,0.6); color: white;
    font-size: 0.75rem; font-weight: 600; padding: 2px 8px; border-radius: 4px;
  }

  .card-body { padding: 16px 18px; display: flex; flex-direction: column; gap: 4px; }
  .card-body h3 { font-size: 0.95rem; font-weight: 700; line-height: 1.3; }
  .instructor { font-size: 0.78rem; color: var(--color-primary); font-weight: 600; }
  .desc { font-size: 0.8rem; color: rgba(68,84,106,0.7); line-height: 1.4; margin-top: 4px; }

  @media (max-width: 900px) { .grid { grid-template-columns: repeat(2, 1fr); } }
  @media (max-width: 768px) { .catalogo { padding: 32px 20px; } }
  @media (max-width: 480px) { .grid { grid-template-columns: 1fr; } }
</style>
