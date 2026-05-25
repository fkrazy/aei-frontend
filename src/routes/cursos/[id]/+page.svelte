<script lang="ts">
  import { base } from '$app/paths';
  import { page } from '$app/stores';
  import Navbar from '$lib/components/Navbar.svelte';
  import logoCanal from '$lib/assets/logo-canal-x-y-yo.png';

  const cursos: Record<string, { titulo: string; categoria: string; precio: number; duracion: string; modulos: string[]; descripcion: string }> = {
    'radiologia-basica': {
      titulo: 'Radiología Básica',
      categoria: 'Radiología',
      precio: 99,
      duracion: '8 horas',
      descripcion: 'Aprende los fundamentos de la radiología convencional, interpretación de placas y protocolos de diagnóstico utilizados en la práctica clínica diaria.',
      modulos: ['Introducción a la radiología', 'Física de los rayos X', 'Anatomía radiológica básica', 'Interpretación de tórax', 'Interpretación de abdomen', 'Huesos y articulaciones', 'Errores comunes', 'Casos clínicos']
    },
    'ultrasonido-avanzado': {
      titulo: 'Ultrasonido Avanzado',
      categoria: 'Ultrasonido',
      precio: 120,
      duracion: '10 horas',
      descripcion: 'Domina las técnicas avanzadas de ultrasonido diagnóstico, incluyendo Doppler color, ecografía musculoesquelética y procedimientos guiados por imagen.',
      modulos: ['Física del ultrasonido', 'Ecografía abdominal', 'Ecografía pélvica', 'Doppler vascular', 'Ultrasonido musculoesquelético', 'Ecografía tiroidea', 'Procedimientos guiados', 'Casos avanzados']
    },
    'tomografia-computada': {
      titulo: 'Tomografía Computada',
      categoria: 'Tomografía',
      precio: 110,
      duracion: '9 horas',
      descripcion: 'Comprende los protocolos de TC, reconstrucciones multiplanares y el análisis sistemático de estudios de tórax, abdomen y cráneo.',
      modulos: ['Principios de TC', 'Protocolos y parámetros', 'TC de tórax', 'TC de abdomen y pelvis', 'TC de cráneo', 'Angiografía por TC', 'Reconstrucciones 3D', 'Casos clínicos']
    },
    'resonancia-magnetica': {
      titulo: 'Resonancia Magnética',
      categoria: 'Resonancia',
      precio: 130,
      duracion: '12 horas',
      descripcion: 'Aprende los fundamentos de la RM, secuencias básicas y avanzadas, y la interpretación de estudios de cerebro, columna y articulaciones.',
      modulos: ['Física de la RM', 'Secuencias básicas', 'RM de cerebro', 'RM de columna', 'RM musculoesquelética', 'RM abdominal', 'Espectroscopía', 'Casos clínicos']
    },
    'pedagogia-digital': {
      titulo: 'Pedagogía Digital',
      categoria: 'Pedagogía',
      precio: 89,
      duracion: '6 horas',
      descripcion: 'Desarrolla habilidades para enseñar medicina usando herramientas digitales, creación de contenido educativo y plataformas de aprendizaje en línea.',
      modulos: ['Fundamentos pedagógicos', 'Herramientas digitales', 'Creación de contenido', 'Grabación y edición', 'Plataformas LMS', 'Evaluación virtual']
    },
    'ia-diagnostico-medico': {
      titulo: 'IA en Diagnóstico Médico',
      categoria: 'IA',
      precio: 149,
      duracion: '14 horas',
      descripcion: 'Explora cómo la inteligencia artificial está transformando el diagnóstico médico por imagen: algoritmos de detección, asistencia al radiólogo y casos reales.',
      modulos: ['Fundamentos de IA en medicina', 'Machine Learning aplicado', 'Redes neuronales convolucionales', 'IA en radiología', 'IA en patología digital', 'Herramientas actuales', 'Ética y regulación', 'El futuro del radiólogo']
    }
  };

  const id = $derived($page.params.id);
  const curso = $derived(cursos[id]);
</script>

<svelte:head>
  <title>{curso ? curso.titulo + ' — AEI' : 'Curso no encontrado'}</title>
</svelte:head>

<div class="page">
  <Navbar />

  {#if curso}
    <div class="hero">
      <div class="hero-inner">
        <div class="logo-glow">
          <img src={logoCanal} alt="Canal X y Yo" class="logo-img" />
        </div>
        <div class="hero-text">
          <span class="badge">{curso.categoria}</span>
          <h1>{curso.titulo}</h1>
          <p class="instructor">Canal X y Yo</p>
          <p class="descripcion">{curso.descripcion}</p>
          <div class="hero-meta">
            <span>⏱ {curso.duracion}</span>
            <span>📚 {curso.modulos.length} módulos</span>
          </div>
        </div>
        <div class="precio-card">
          <p class="precio">${curso.precio} <span>USD</span></p>
          <button class="btn-comprar">Inscribirse ahora</button>
          <a href="{base}/cursos" class="btn-volver">← Volver al catálogo</a>
        </div>
      </div>
    </div>

    <div class="contenido">
      <div class="container">
        <h2 class="gold">Contenido del curso</h2>
        <div class="modulos">
          {#each curso.modulos as modulo, i}
            <div class="modulo-row">
              <span class="modulo-num">{String(i + 1).padStart(2, '0')}</span>
              <span class="modulo-titulo">{modulo}</span>
            </div>
          {/each}
        </div>
      </div>
    </div>

  {:else}
    <div class="not-found">
      <h2>Curso no encontrado</h2>
      <a href="{base}/cursos" class="btn-volver">← Ver todos los cursos</a>
    </div>
  {/if}
</div>

<style>
  .page { background: var(--color-primary); min-height: 100vh; color: white; font-family: var(--font-family); }

  .hero { background: var(--color-primary-dark); padding: 60px 32px; }
  .hero-inner {
    max-width: 1200px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: auto 1fr auto;
    gap: 48px;
    align-items: start;
  }
  .logo-glow { border-radius: 50%; box-shadow: 0 0 40px 20px rgba(255,255,255,0.35); flex-shrink: 0; }
  .logo-img { width: 120px; height: 120px; border-radius: 50%; object-fit: cover; display: block; }

  .badge { background: var(--color-accent-gold); color: var(--color-text-dark); font-size: 0.75rem; font-weight: 700; padding: 4px 12px; border-radius: 999px; display: inline-block; margin-bottom: 12px; }
  .hero-text h1 { font-size: 2rem; font-weight: 700; margin-bottom: 8px; }
  .instructor { color: var(--color-accent-gold); font-weight: 600; font-size: 0.95rem; margin-bottom: 16px; }
  .descripcion { color: rgba(255,255,255,0.85); line-height: 1.7; margin-bottom: 20px; }
  .hero-meta { display: flex; gap: 24px; color: rgba(255,255,255,0.7); font-size: 0.9rem; }
  .gold { color: var(--color-accent-gold); }

  .precio-card {
    background: rgba(0,0,0,0.2);
    border-radius: 12px;
    padding: 28px 24px;
    display: flex;
    flex-direction: column;
    gap: 16px;
    min-width: 220px;
    text-align: center;
  }
  .precio { font-size: 2rem; font-weight: 700; }
  .precio span { font-size: 1rem; color: rgba(255,255,255,0.6); }
  .btn-comprar {
    background: var(--color-accent-gold);
    color: var(--color-text-dark);
    border: none;
    padding: 14px 24px;
    border-radius: 8px;
    font-weight: 700;
    font-size: 1rem;
    cursor: pointer;
    transition: opacity 0.2s;
  }
  .btn-comprar:hover { opacity: 0.9; }
  .btn-volver { color: rgba(255,255,255,0.6); font-size: 0.875rem; text-decoration: none; }
  .btn-volver:hover { color: white; }

  .contenido { padding: 60px 32px; }
  .container { max-width: 1200px; margin: 0 auto; }
  .contenido h2 { font-size: 1.5rem; font-weight: 700; margin-bottom: 32px; }

  .modulos { display: flex; flex-direction: column; gap: 2px; }
  .modulo-row {
    display: flex;
    align-items: center;
    gap: 20px;
    padding: 16px 24px;
    background: rgba(255,255,255,0.06);
    border-radius: 8px;
    transition: background 0.2s;
  }
  .modulo-row:hover { background: rgba(255,255,255,0.12); }
  .modulo-num { color: var(--color-accent-gold); font-weight: 700; font-size: 0.85rem; min-width: 28px; }
  .modulo-titulo { color: white; font-size: 0.95rem; }

  .not-found { display: flex; flex-direction: column; align-items: center; justify-content: center; min-height: 60vh; gap: 24px; }

  @media (max-width: 900px) {
    .hero-inner { grid-template-columns: 1fr; gap: 32px; }
    .logo-glow { display: none; }
    .precio-card { min-width: unset; }
  }
  @media (max-width: 768px) {
    .hero { padding: 40px 20px; }
    .contenido { padding: 40px 20px; }
  }
</style>
