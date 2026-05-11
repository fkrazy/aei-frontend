<script lang="ts">
  import { base } from '$app/paths';
</script>

<div class="selector">
  <h1>AEI — Propuestas de Diseño</h1>
  <p>Selecciona una propuesta para previsualizar</p>
  <div class="opciones">
    <a href="{base}/propuesta-a" class="opcion opcion-a">
      <span class="tag">Propuesta A</span>
      <h2>Fiel al cliente</h2>
      <p>Fondo azul dominante, estilo visual del PPT original adaptado a web. Respeta 100% la visión del cliente.</p>
      <ul>
        <li>Fondo azul #4472C4 en toda la página</li>
        <li>Logos con glow blanco como hero</li>
        <li>Títulos en amarillo dorado</li>
        <li>Botones outline blancos</li>
      </ul>
      <span class="cta">Ver Propuesta A →</span>
    </a>

    <a href="{base}/propuesta-b" class="opcion opcion-b">
      <span class="tag">Propuesta B</span>
      <h2>Recomendación experta</h2>
      <p>AEI como marca protagonista. Azul como acento estratégico, layout moderno que convierte mejor.</p>
      <ul>
        <li>AEI hero principal, Canal X y Yo como respaldo</li>
        <li>Fondos alternados para respirar</li>
        <li>CTA claro desde el primer scroll</li>
        <li>Navegación web estándar</li>
      </ul>
      <span class="cta">Ver Propuesta B →</span>
    </a>
  </div>
</div>

<style>
  .selector {
    min-height: 100vh;
    background: #1a1a2e;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 60px 24px;
    gap: 32px;
  }

  .selector h1 {
    font-size: 2rem;
    font-weight: 700;
    color: #FFC000;
    text-align: center;
  }

  .selector > p {
    color: rgba(255,255,255,0.6);
    font-size: 1.1rem;
  }

  .opciones {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 32px;
    max-width: 900px;
    width: 100%;
  }

  .opcion {
    background: rgba(255,255,255,0.05);
    border: 2px solid rgba(255,255,255,0.15);
    border-radius: 16px;
    padding: 36px 32px;
    display: flex;
    flex-direction: column;
    gap: 16px;
    cursor: pointer;
    transition: border-color 0.2s, transform 0.2s;
  }

  .opcion:hover { transform: translateY(-4px); }
  .opcion-a:hover { border-color: #4472C4; }
  .opcion-b:hover { border-color: #FFC000; }

  .tag {
    font-size: 0.75rem;
    font-weight: 700;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    padding: 4px 10px;
    border-radius: 999px;
    width: fit-content;
  }

  .opcion-a .tag { background: #4472C4; color: white; }
  .opcion-b .tag { background: #FFC000; color: #44546A; }

  .opcion h2 { font-size: 1.4rem; font-weight: 700; color: white; }

  .opcion p { color: rgba(255,255,255,0.65); font-size: 0.95rem; line-height: 1.6; }

  .opcion ul { list-style: none; display: flex; flex-direction: column; gap: 8px; }

  .opcion ul li {
    color: rgba(255,255,255,0.5);
    font-size: 0.875rem;
    padding-left: 16px;
    position: relative;
  }

  .opcion ul li::before { content: '·'; position: absolute; left: 0; color: rgba(255,255,255,0.3); }

  .cta { margin-top: auto; font-weight: 600; font-size: 0.95rem; }
  .opcion-a .cta { color: #5B9BD5; }
  .opcion-b .cta { color: #FFC000; }

  @media (max-width: 640px) {
    .opciones { grid-template-columns: 1fr; }
  }
</style>
