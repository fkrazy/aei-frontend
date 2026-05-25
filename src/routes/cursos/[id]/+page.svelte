<script lang="ts">
  import { base } from '$app/paths';
  import { page } from '$app/stores';
  import Navbar from '$lib/components/Navbar.svelte';
  import logoCanal from '$lib/assets/logo-canal-x-y-yo.png';

  const productos: Record<string, { titulo: string; categoria: string; precio: number; descripcion: string }> = {
    'radiologia-basica':      { titulo: 'Radiología Básica',        categoria: 'Radiología',  precio: 99,  descripcion: 'Fundamentos de radiología convencional e interpretación de imágenes para el diagnóstico médico.' },
    'ultrasonido-avanzado':   { titulo: 'Ultrasonido Avanzado',     categoria: 'Ultrasonido', precio: 120, descripcion: 'Técnicas avanzadas de ultrasonido diagnóstico y procedimientos guiados por imagen.' },
    'tomografia-computada':   { titulo: 'Tomografía Computada',     categoria: 'Tomografía',  precio: 110, descripcion: 'Protocolos de TC y análisis sistemático de estudios de tórax, abdomen y cráneo.' },
    'resonancia-magnetica':   { titulo: 'Resonancia Magnética',     categoria: 'Resonancia',  precio: 130, descripcion: 'Secuencias de RM y interpretación de estudios de cerebro, columna y articulaciones.' },
    'pedagogia-digital':      { titulo: 'Pedagogía Digital',        categoria: 'Pedagogía',   precio: 89,  descripcion: 'Herramientas y estrategias para enseñar medicina usando plataformas digitales.' },
    'ia-diagnostico-medico':  { titulo: 'IA en Diagnóstico Médico', categoria: 'IA',          precio: 149, descripcion: 'Cómo la inteligencia artificial está transformando el diagnóstico médico por imagen.' },
  };

  const id = $derived($page.params.id);
  const producto = $derived(productos[id]);
</script>

<svelte:head>
  <title>{producto ? producto.titulo + ' — AEI' : 'Producto no encontrado'}</title>
</svelte:head>

<div class="page">
  <Navbar />

  {#if producto}
    <div class="container">
      <a href="{base}/cursos" class="back">← Volver al catálogo</a>

      <div class="producto">
        <div class="producto-img">
          <img src={logoCanal} alt={producto.titulo} class="logo-img" />
        </div>

        <div class="producto-info">
          <span class="badge">{producto.categoria}</span>
          <h1>{producto.titulo}</h1>
          <p class="instructor">Canal X y Yo</p>
          <p class="descripcion">{producto.descripcion}</p>

          <div class="compra">
            <span class="precio">${producto.precio} <small>USD</small></span>
            <button class="btn-comprar">Comprar ahora</button>
          </div>
        </div>
      </div>
    </div>

  {:else}
    <div class="not-found">
      <h2>Producto no encontrado</h2>
      <a href="{base}/cursos" class="btn-comprar">← Ver catálogo</a>
    </div>
  {/if}
</div>

<style>
  .page { background: var(--color-primary); min-height: 100vh; color: white; font-family: var(--font-family); }

  .container { max-width: 900px; margin: 0 auto; padding: 48px 32px; }

  .back { color: rgba(255,255,255,0.6); text-decoration: none; font-size: 0.875rem; display: inline-block; margin-bottom: 40px; }
  .back:hover { color: white; }

  .producto {
    display: grid;
    grid-template-columns: 280px 1fr;
    gap: 56px;
    align-items: start;
  }

  .producto-img {
    background: var(--color-primary-dark);
    border-radius: 16px;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 48px 32px;
  }
  .logo-img { width: 180px; height: 180px; border-radius: 50%; object-fit: cover; box-shadow: 0 0 40px 20px rgba(255,255,255,0.25); }

  .producto-info { display: flex; flex-direction: column; gap: 16px; }
  .badge { background: var(--color-accent-gold); color: var(--color-text-dark); font-size: 0.75rem; font-weight: 700; padding: 4px 12px; border-radius: 999px; width: fit-content; }
  h1 { font-size: 2rem; font-weight: 700; line-height: 1.2; }
  .instructor { color: var(--color-accent-gold); font-weight: 600; font-size: 0.95rem; }
  .descripcion { color: rgba(255,255,255,0.85); line-height: 1.7; font-size: 1rem; }

  .compra { display: flex; align-items: center; gap: 24px; margin-top: 8px; padding-top: 24px; border-top: 1px solid rgba(255,255,255,0.15); }
  .precio { font-size: 2rem; font-weight: 700; }
  .precio small { font-size: 1rem; color: rgba(255,255,255,0.5); }
  .btn-comprar { background: var(--color-accent-gold); color: var(--color-text-dark); border: none; padding: 14px 32px; border-radius: 8px; font-weight: 700; font-size: 1rem; cursor: pointer; transition: opacity 0.2s; text-decoration: none; }
  .btn-comprar:hover { opacity: 0.9; }

  .not-found { display: flex; flex-direction: column; align-items: center; justify-content: center; min-height: 60vh; gap: 24px; }

  @media (max-width: 768px) {
    .container { padding: 32px 20px; }
    .producto { grid-template-columns: 1fr; gap: 32px; }
    .producto-img { padding: 32px; }
    .compra { flex-direction: column; align-items: flex-start; }
  }
</style>
