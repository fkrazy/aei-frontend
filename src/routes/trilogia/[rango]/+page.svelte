<script lang="ts">
  import { base } from '$app/paths';
  import { page } from '$app/stores';
  import Navbar from '$lib/components/Navbar.svelte';
  import logoAei from '$lib/assets/logo-aei.png';

  const rangos: Record<string, { label: string }> = {
    '0-1':       { label: '0 a 1 año' },
    '1-3':       { label: '1 a 3 años' },
    '4-6':       { label: '4 a 6 años' },
    '7-10':      { label: '7 a 10 años' },
    '11-15':     { label: '11 a 15 años' },
    '16-20':     { label: '16 a 20 años' },
    'abuelitos': { label: 'Abuelitos' },
  };

  const paquetes: Record<string, { id: string; titulo: string; descripcion: string; precio: number }[]> = {
    '0-1': [
      { id: 'despertar-musical',  titulo: 'Despertar Musical',  descripcion: 'Estimulación auditiva y visual para bebés con canciones suaves y cuentos ilustrados.',  precio: 45 },
      { id: 'mundo-de-colores',   titulo: 'Mundo de Colores',   descripcion: 'Exploración sensorial a través del color, el ritmo y la narración para los primeros meses.', precio: 45 },
    ],
    '1-3': [
      { id: 'primeras-palabras',  titulo: 'Primeras Palabras',  descripcion: 'Canciones y cuentos para estimular el lenguaje en la etapa más crítica del desarrollo.',  precio: 45 },
      { id: 'juego-y-movimiento', titulo: 'Juego y Movimiento', descripcion: 'Ritmo, danza y narración para niños que empiezan a explorar el mundo.', precio: 45 },
    ],
    '4-6': [
      { id: 'aventura-creativa',  titulo: 'Aventura Creativa',  descripcion: 'Imaginación y aprendizaje lúdico para preescolares con canciones, video y storybook.', precio: 45 },
      { id: 'cuentos-magicos',    titulo: 'Cuentos Mágicos',    descripcion: 'Historias ilustradas con música original para despertar el amor por la lectura.', precio: 45 },
    ],
    '7-10': [
      { id: 'exploradores',       titulo: 'Exploradores',       descripcion: 'Contenido educativo y creativo para niños curiosos que quieren entender el mundo.', precio: 45 },
      { id: 'ritmo-y-ciencia',    titulo: 'Ritmo y Ciencia',    descripcion: 'Aprende conceptos científicos a través de canciones, animaciones y cuentos.', precio: 45 },
    ],
    '11-15': [
      { id: 'identidad-digital',  titulo: 'Identidad Digital',  descripcion: 'Arte, tecnología y narrativa para adolescentes que construyen su voz propia.', precio: 45 },
      { id: 'voces-jovenes',      titulo: 'Voces Jóvenes',      descripcion: 'Expresión creativa a través de la música, el video y la escritura.', precio: 45 },
    ],
    '16-20': [
      { id: 'arte-y-proposito',   titulo: 'Arte y Propósito',   descripcion: 'Recursos artísticos para jóvenes en búsqueda de su camino creativo y profesional.', precio: 45 },
      { id: 'narrativas-propias', titulo: 'Narrativas Propias', descripcion: 'Canción, video y storybook para contar tu historia con intención y autenticidad.', precio: 45 },
    ],
    'abuelitos': [
      { id: 'memorias-vivas',     titulo: 'Memorias Vivas',     descripcion: 'Canciones y cuentos para revivir emociones y mantener activa la mente.', precio: 45 },
      { id: 'sabiduria-activa',   titulo: 'Sabiduría Activa',   descripcion: 'Arte y narrativa diseñados para el aprendizaje pleno en la tercera edad.', precio: 45 },
    ],
  };

  const rangoSlug = $derived($page.params.rango);
  const rangoInfo = $derived(rangos[rangoSlug]);
  const listado = $derived(paquetes[rangoSlug] ?? []);
</script>

<svelte:head>
  <title>{rangoInfo ? 'Trilogía · ' + rangoInfo.label : 'Trilogía AEI'} — AEI</title>
  <meta name="description" content={rangoInfo ? 'Paquetes de Trilogía AEI para ' + rangoInfo.label + '. Canción, Video y Storybook.' : 'Trilogía AEI.'} />
</svelte:head>

<div class="page">
  <Navbar />

  {#if rangoInfo}
    <div class="hero">
      <div class="hero-inner">
        <div class="logo-glow">
          <img src={logoAei} alt="AEI" class="logo-img" />
        </div>
        <div class="hero-text">
          <span class="badge">Trilogía AEI</span>
          <h1>Paquetes <span class="gold">{rangoInfo.label}</span></h1>
          <p>Canción + Video + Storybook — aprendizaje con inteligencia artificial para esta etapa.</p>
        </div>
      </div>
    </div>

    <div class="catalogo">
      <div class="container">
        <a href="{base}/#trilogia" class="back">← Volver a Trilogía</a>
        <div class="grid">
          {#each listado as paquete}
            <a href="{base}/trilogia/{rangoSlug}/{paquete.id}" class="card">
              <div class="card-thumb">
                <img src={logoAei} alt={paquete.titulo} class="thumb-img" />
                <span class="badge-card">{rangoInfo.label}</span>
              </div>
              <div class="card-body">
                <h3>{paquete.titulo}</h3>
                <p class="instructor">AEI — Arte Educación Inteligente</p>
                <div class="card-footer">
                  <span class="precio">${paquete.precio} USD</span>
                  <span class="cta">Ver más →</span>
                </div>
              </div>
            </a>
          {/each}
        </div>
      </div>
    </div>

  {:else}
    <div class="not-found">
      <h2>Rango no encontrado</h2>
      <a href="{base}/#trilogia" class="btn-back">← Ver Trilogía</a>
    </div>
  {/if}
</div>

<style>
  .page { background: var(--color-primary); min-height: 100vh; color: white; font-family: var(--font-family); }

  .hero { background: var(--color-primary-dark); padding: 60px 32px; }
  .hero-inner { max-width: 1200px; margin: 0 auto; display: flex; align-items: center; gap: 48px; }
  .logo-glow { border-radius: 50%; box-shadow: 0 0 40px 20px rgba(255,255,255,0.35); flex-shrink: 0; }
  .logo-img { width: 140px; height: 140px; border-radius: 50%; object-fit: cover; display: block; }
  .badge { background: var(--color-accent-gold); color: var(--color-text-dark); font-size: 0.75rem; font-weight: 700; padding: 4px 12px; border-radius: 999px; display: inline-block; margin-bottom: 12px; }
  .hero-text h1 { font-size: 2.25rem; font-weight: 700; margin-bottom: 12px; }
  .hero-text p { color: rgba(255,255,255,0.8); font-size: 1.05rem; line-height: 1.7; max-width: 500px; }
  .gold { color: var(--color-accent-gold); }

  .catalogo { padding: 60px 32px; }
  .container { max-width: 1200px; margin: 0 auto; }
  .back { color: rgba(255,255,255,0.6); text-decoration: none; font-size: 0.875rem; display: inline-block; margin-bottom: 40px; }
  .back:hover { color: white; }

  .grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 24px; }

  .card { background: white; border-radius: 12px; overflow: hidden; text-decoration: none; color: var(--color-text-dark); box-shadow: 0 2px 8px rgba(0,0,0,0.12); transition: transform 0.2s, box-shadow 0.2s; display: flex; flex-direction: column; }
  .card:hover { transform: translateY(-4px); box-shadow: 0 8px 24px rgba(0,0,0,0.2); }

  .card-thumb { position: relative; aspect-ratio: 16/9; overflow: hidden; background: var(--color-primary-dark); display: flex; align-items: center; justify-content: center; }
  .thumb-img { width: 80px; height: 80px; border-radius: 50%; object-fit: cover; }
  .badge-card { position: absolute; top: 12px; left: 12px; background: var(--color-accent-gold); color: var(--color-text-dark); font-size: 0.7rem; font-weight: 700; padding: 3px 10px; border-radius: 999px; }

  .card-body { padding: 20px; display: flex; flex-direction: column; gap: 8px; flex: 1; }
  .card-body h3 { font-size: 1rem; font-weight: 700; color: var(--color-text-dark); }
  .instructor { font-size: 0.8rem; color: var(--color-primary); font-weight: 600; }
  .card-footer { display: flex; justify-content: space-between; align-items: center; margin-top: auto; padding-top: 12px; border-top: 1px solid #eee; }
  .precio { font-size: 1.1rem; font-weight: 700; color: var(--color-text-dark); }
  .cta { font-size: 0.875rem; font-weight: 600; color: var(--color-primary); }

  .not-found { display: flex; flex-direction: column; align-items: center; justify-content: center; min-height: 60vh; gap: 24px; }
  .btn-back { color: white; text-decoration: none; }

  @media (max-width: 900px) { .grid { grid-template-columns: repeat(2, 1fr); } }
  @media (max-width: 768px) {
    .hero { padding: 40px 20px; }
    .hero-inner { flex-direction: column; gap: 24px; text-align: center; }
    .hero-text p { max-width: 100%; }
    .catalogo { padding: 40px 20px; }
  }
  @media (max-width: 480px) { .grid { grid-template-columns: 1fr; } }
</style>
