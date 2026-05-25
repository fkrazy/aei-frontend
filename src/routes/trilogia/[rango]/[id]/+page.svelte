<script lang="ts">
  import { base } from '$app/paths';
  import { page } from '$app/stores';
  import Navbar from '$lib/components/Navbar.svelte';
  import logoAei from '$lib/assets/logo-aei.png';
  import Icon from '@iconify/svelte';

  const rangos: Record<string, string> = {
    '0-1': '0 a 1 año', '1-3': '1 a 3 años', '4-6': '4 a 6 años',
    '7-10': '7 a 10 años', '11-15': '11 a 15 años', '16-20': '16 a 20 años',
    'abuelitos': 'Abuelitos',
  };

  const paquetes: Record<string, { titulo: string; descripcion: string }> = {
    'despertar-musical':  { titulo: 'Despertar Musical',  descripcion: 'Estimulación auditiva y visual para bebés con canciones suaves y cuentos ilustrados.' },
    'mundo-de-colores':   { titulo: 'Mundo de Colores',   descripcion: 'Exploración sensorial a través del color, el ritmo y la narración para los primeros meses.' },
    'primeras-palabras':  { titulo: 'Primeras Palabras',  descripcion: 'Canciones y cuentos para estimular el lenguaje en la etapa más crítica del desarrollo.' },
    'juego-y-movimiento': { titulo: 'Juego y Movimiento', descripcion: 'Ritmo, danza y narración para niños que empiezan a explorar el mundo.' },
    'aventura-creativa':  { titulo: 'Aventura Creativa',  descripcion: 'Imaginación y aprendizaje lúdico para preescolares con canciones, video y storybook.' },
    'cuentos-magicos':    { titulo: 'Cuentos Mágicos',    descripcion: 'Historias ilustradas con música original para despertar el amor por la lectura.' },
    'exploradores':       { titulo: 'Exploradores',       descripcion: 'Contenido educativo y creativo para niños curiosos que quieren entender el mundo.' },
    'ritmo-y-ciencia':    { titulo: 'Ritmo y Ciencia',    descripcion: 'Aprende conceptos científicos a través de canciones, animaciones y cuentos.' },
    'identidad-digital':  { titulo: 'Identidad Digital',  descripcion: 'Arte, tecnología y narrativa para adolescentes que construyen su voz propia.' },
    'voces-jovenes':      { titulo: 'Voces Jóvenes',      descripcion: 'Expresión creativa a través de la música, el video y la escritura.' },
    'arte-y-proposito':   { titulo: 'Arte y Propósito',   descripcion: 'Recursos artísticos para jóvenes en búsqueda de su camino creativo y profesional.' },
    'narrativas-propias': { titulo: 'Narrativas Propias', descripcion: 'Canción, video y storybook para contar tu historia con intención y autenticidad.' },
    'memorias-vivas':     { titulo: 'Memorias Vivas',     descripcion: 'Canciones y cuentos para revivir emociones y mantener activa la mente.' },
    'sabiduria-activa':   { titulo: 'Sabiduría Activa',   descripcion: 'Arte y narrativa diseñados para el aprendizaje pleno en la tercera edad.' },
  };

  const subproductos = [
    { id: 'cancion',   titulo: 'Canción',   icon: 'mdi:music',                    precio: 15, descripcion: 'Canción educativa original con letra, música y recursos pedagógicos.' },
    { id: 'video',     titulo: 'Video',     icon: 'mdi:video',                    precio: 20, descripcion: 'Video animado adaptado a la edad con contenido curricular y visual.' },
    { id: 'storybook', titulo: 'Storybook', icon: 'mdi:book-open-page-variant',   precio: 18, descripcion: 'Libro ilustrado digital con narración y actividades descargables.' },
  ];

  const rangoSlug = $derived($page.params.rango);
  const id = $derived($page.params.id);
  const rangoLabel = $derived(rangos[rangoSlug]);
  const paquete = $derived(paquetes[id]);
</script>

<svelte:head>
  <title>{paquete ? paquete.titulo + ' — AEI' : 'Paquete no encontrado'}</title>
  <meta name="description" content={paquete ? paquete.descripcion : ''} />
</svelte:head>

<div class="page">
  <Navbar />

  {#if paquete && rangoLabel}
    <div class="container">
      <a href="{base}/trilogia/{rangoSlug}" class="back">← Volver a {rangoLabel}</a>

      <div class="producto">
        <div class="producto-img">
          <img src={logoAei} alt={paquete.titulo} class="logo-img" />
        </div>

        <div class="producto-info">
          <span class="badge">{rangoLabel}</span>
          <h1>{paquete.titulo}</h1>
          <p class="instructor">AEI — Arte Educación Inteligente</p>
          <p class="descripcion">{paquete.descripcion}</p>
        </div>
      </div>

      <div class="subproductos">
        <h2 class="sub-titulo">Elige tu formato</h2>
        <div class="sub-grid">
          {#each subproductos as sub}
            <div class="sub-card">
              <div class="sub-icon"><Icon icon={sub.icon} width="32" height="32" /></div>
              <div class="sub-body">
                <h3>{sub.titulo}</h3>
                <p>{sub.descripcion}</p>
              </div>
              <div class="sub-footer">
                <span class="precio">${sub.precio} <small>USD</small></span>
                <button class="btn-comprar">Comprar</button>
              </div>
            </div>
          {/each}
        </div>

        <div class="bundle">
          <div class="bundle-text">
            <h3>Trilogía Completa</h3>
            <p>Canción + Video + Storybook — ahorra 15%</p>
          </div>
          <div class="bundle-footer">
            <span class="precio gold">$45 <small>USD</small></span>
            <button class="btn-comprar gold">Comprar pack</button>
          </div>
        </div>
      </div>
    </div>

  {:else}
    <div class="not-found">
      <h2>Paquete no encontrado</h2>
      <a href="{base}/#trilogia" class="btn-comprar">← Ver Trilogía</a>
    </div>
  {/if}
</div>

<style>
  .page { background: var(--color-primary); min-height: 100vh; color: white; font-family: var(--font-family); }

  .container { max-width: 900px; margin: 0 auto; padding: 48px 32px; }

  .back { color: rgba(255,255,255,0.6); text-decoration: none; font-size: 0.875rem; display: inline-block; margin-bottom: 40px; }
  .back:hover { color: white; }

  .producto { display: grid; grid-template-columns: 280px 1fr; gap: 56px; align-items: start; }

  .producto-img { background: var(--color-primary-dark); border-radius: 16px; display: flex; align-items: center; justify-content: center; padding: 48px 32px; }
  .logo-img { width: 180px; height: 180px; border-radius: 50%; object-fit: cover; box-shadow: 0 0 40px 20px rgba(255,255,255,0.25); }

  .producto-info { display: flex; flex-direction: column; gap: 16px; }
  .badge { background: var(--color-accent-gold); color: var(--color-text-dark); font-size: 0.75rem; font-weight: 700; padding: 4px 12px; border-radius: 999px; width: fit-content; }
  h1 { font-size: 2rem; font-weight: 700; line-height: 1.2; }
  .instructor { color: var(--color-accent-gold); font-weight: 600; font-size: 0.95rem; }
  .descripcion { color: rgba(255,255,255,0.85); line-height: 1.7; font-size: 1rem; }

  /* Sub-productos */
  .subproductos { margin-top: 56px; }
  .sub-titulo { font-size: 1.1rem; font-weight: 700; color: var(--color-accent-gold); text-transform: uppercase; letter-spacing: 0.08em; margin-bottom: 20px; }

  .sub-grid { display: flex; flex-direction: column; gap: 12px; }

  .sub-card {
    background: var(--color-primary-dark);
    border-radius: var(--radius-card);
    padding: 20px 24px;
    display: grid;
    grid-template-columns: 48px 1fr auto;
    gap: 16px;
    align-items: center;
    border: 1px solid rgba(255,255,255,0.1);
    transition: border-color 0.2s;
  }
  .sub-card:hover { border-color: rgba(255,255,255,0.3); }
  .sub-icon { display: flex; align-items: center; justify-content: center; color: var(--color-accent-gold); }
  .sub-body { display: flex; flex-direction: column; gap: 4px; }
  .sub-body h3 { font-size: 1.05rem; font-weight: 700; }
  .sub-body p { font-size: 0.8rem; color: rgba(255,255,255,0.65); line-height: 1.5; }
  .sub-footer { display: flex; flex-direction: column; align-items: flex-end; gap: 8px; min-width: 110px; }

  .precio { font-size: 1.3rem; font-weight: 700; white-space: nowrap; }
  .precio small { font-size: 0.75rem; color: rgba(255,255,255,0.5); }
  .precio.gold { color: var(--color-accent-gold); }

  .btn-comprar {
    background: var(--color-accent-gold);
    color: var(--color-text-dark);
    border: none;
    padding: 10px 20px;
    border-radius: 8px;
    font-weight: 700;
    font-size: 0.875rem;
    cursor: pointer;
    transition: opacity 0.2s;
    white-space: nowrap;
    text-decoration: none;
  }
  .btn-comprar:hover { opacity: 0.9; }

  .bundle {
    background: rgba(255, 192, 0, 0.08);
    border: 2px solid var(--color-accent-gold);
    border-radius: var(--radius-card);
    padding: 20px 24px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 16px;
    margin-top: 16px;
  }
  .bundle-text h3 { font-size: 1.1rem; font-weight: 700; color: var(--color-accent-gold); }
  .bundle-text p { font-size: 0.8rem; color: rgba(255,255,255,0.65); margin-top: 4px; }
  .bundle-footer { display: flex; flex-direction: column; align-items: flex-end; gap: 8px; }

  .not-found { display: flex; flex-direction: column; align-items: center; justify-content: center; min-height: 60vh; gap: 24px; }

  @media (max-width: 768px) {
    .container { padding: 32px 20px; }
    .producto { grid-template-columns: 1fr; gap: 32px; }
    .producto-img { padding: 32px; }
    .sub-card { grid-template-columns: 40px 1fr; grid-template-rows: auto auto; }
    .sub-footer { grid-column: 1 / -1; flex-direction: row; justify-content: space-between; align-items: center; padding-top: 12px; border-top: 1px solid rgba(255,255,255,0.1); }
    .bundle { flex-direction: column; align-items: flex-start; }
    .bundle-footer { flex-direction: row; align-items: center; justify-content: space-between; width: 100%; }
  }
</style>
