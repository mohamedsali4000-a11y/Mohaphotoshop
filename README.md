<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="MohaPhoto: edición de fotos y diseño gráfico personalizado.">
  <title>MohaPhoto | Edición y diseño</title>

  <style>
    :root {
      --bg: #101117;
      --surface: #191b25;
      --surface-light: #20232f;
      --text: #f7f7fa;
      --muted: #b9bdc9;
      --accent: #ff6b73;
      --accent-light: #ffc773;
      --border: rgba(255,255,255,.1);
      --green: #25d366;
      --radius: 22px;
      --shadow: 0 18px 45px rgba(0,0,0,.25);
    }

    * { box-sizing: border-box; }

    html {
      scroll-behavior: smooth;
      scroll-padding-top: 85px;
    }

    body {
      margin: 0;
      background: linear-gradient(135deg, var(--bg), #171a24);
      color: var(--text);
      font-family: Arial, Helvetica, sans-serif;
      line-height: 1.7;
    }

    body[dir="rtl"] {
      text-align: right;
    }

    a {
      color: inherit;
      text-decoration: none;
    }

    button {
      font: inherit;
    }

    .container {
      width: min(1120px, calc(100% - 32px));
      margin: 0 auto;
    }

    .header {
      position: sticky;
      top: 0;
      z-index: 20;
      background: rgba(16,17,23,.9);
      border-bottom: 1px solid var(--border);
      backdrop-filter: blur(12px);
    }

    .nav {
      min-height: 72px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 20px;
    }

    .logo {
      font-weight: 800;
      font-size: 1.65rem;
      letter-spacing: .02em;
      white-space: nowrap;
    }

    .logo span,
    .gradient-text {
      background: linear-gradient(90deg, var(--accent), var(--accent-light));
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
    }

    .nav-links {
      display: flex;
      align-items: center;
      gap: 20px;
      color: var(--muted);
      font-size: .92rem;
    }

    .nav-links a:hover {
      color: var(--text);
    }

    .languages {
      display: flex;
      gap: 7px;
      flex-wrap: wrap;
    }

    .language-button {
      border: 1px solid var(--border);
      border-radius: 999px;
      background: transparent;
      color: var(--text);
      cursor: pointer;
      padding: 8px 11px;
      font-size: .82rem;
    }

    .language-button.active {
      background: linear-gradient(90deg, var(--accent), var(--accent-light));
      color: #141414;
      border-color: transparent;
      font-weight: 700;
    }

    .hero {
      padding: 76px 0 50px;
    }

    .hero-grid {
      display: grid;
      grid-template-columns: 1.1fr .9fr;
      align-items: center;
      gap: 38px;
    }

    .eyebrow {
      display: inline-block;
      margin-bottom: 18px;
      padding: 8px 13px;
      border: 1px solid var(--border);
      border-radius: 999px;
      color: var(--muted);
      background: rgba(255,255,255,.035);
      font-size: .86rem;
    }

    h1 {
      margin: 0 0 18px;
      font-size: clamp(2.6rem, 6vw, 5rem);
      line-height: 1.08;
      letter-spacing: -.055em;
    }

    .hero-text {
      max-width: 650px;
      margin: 0 0 25px;
      color: var(--muted);
      font-size: 1.08rem;
    }

    .button-row {
      display: flex;
      flex-wrap: wrap;
      gap: 12px;
      margin-bottom: 18px;
    }

    .button {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      min-height: 48px;
      padding: 12px 19px;
      border-radius: 12px;
      border: 1px solid transparent;
      font-weight: 700;
      transition: transform .2s ease, opacity .2s ease;
    }

    .button:hover {
      transform: translateY(-2px);
      opacity: .94;
    }

    .button-primary {
      background: linear-gradient(90deg, var(--accent), var(--accent-light));
      color: #151515;
    }

    .button-outline {
      border-color: var(--border);
      background: transparent;
      color: var(--text);
    }

    .price-note {
      display: inline-flex;
      align-items: center;
      gap: 9px;
      padding: 10px 14px;
      border: 1px solid var(--border);
      border-radius: 12px;
      background: rgba(255,255,255,.035);
      color: var(--muted);
    }

    .price-note strong {
      color: var(--text);
      font-size: 1.1rem;
    }

    .hero-image-wrap {
      position: relative;
    }

    .hero-image {
      width: 100%;
      height: 440px;
      object-fit: cover;
      border: 1px solid var(--border);
      border-radius: 28px;
      box-shadow: var(--shadow);
    }

    .image-label {
      position: absolute;
      left: 18px;
      bottom: 18px;
      padding: 12px 15px;
      border: 1px solid var(--border);
      border-radius: 14px;
      background: rgba(16,17,23,.84);
      color: var(--text);
    }

    body[dir="rtl"] .image-label {
      left: auto;
      right: 18px;
    }

    section {
      padding: 42px 0;
    }

    .section-heading {
      margin-bottom: 25px;
    }

    h2 {
      margin: 0 0 10px;
      font-size: clamp(1.9rem, 4vw, 2.8rem);
      letter-spacing: -.04em;
    }

    .section-description {
      max-width: 680px;
      margin: 0;
      color: var(--muted);
    }

    .services-grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 17px;
    }

    .service-card {
      padding: 22px;
      border: 1px solid var(--border);
      border-radius: var(--radius);
      background: rgba(255,255,255,.035);
      box-shadow: var(--shadow);
    }

    .service-icon {
      display: grid;
      place-items: center;
      width: 48px;
      height: 48px;
      margin-bottom: 14px;
      border-radius: 15px;
      background: linear-gradient(135deg, var(--accent), var(--accent-light));
      color: #151515;
      font-size: 1.35rem;
      font-weight: 800;
    }

    .service-card h3 {
      margin: 0 0 8px;
      font-size: 1.12rem;
    }

    .service-card p {
      margin: 0;
      color: var(--muted);
    }

    .gallery-grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 17px;
    }

    .gallery-card {
      overflow: hidden;
      border: 1px solid var(--border);
      border-radius: var(--radius);
      background: var(--surface);
    }

    .gallery-card img {
      width: 100%;
      height: 260px;
      object-fit: cover;
      transition: transform .35s ease;
    }

    .gallery-card:hover img {
      transform: scale(1.04);
    }

    .gallery-caption {
      padding: 15px 17px 18px;
    }

    .gallery-caption h3 {
      margin: 0 0 5px;
      font-size: 1.08rem;
    }

    .gallery-caption p {
      margin: 0;
      color: var(--muted);
      font-size: .94rem;
    }

    .price-card {
      display: grid;
      grid-template-columns: 1fr auto;
      align-items: center;
      gap: 22px;
      padding: 28px;
      border: 1px solid rgba(255,199,115,.35);
      border-radius: 26px;
      background: linear-gradient(120deg, rgba(255,107,115,.1), rgba(255,199,115,.08));
    }

    .price-card h3 {
      margin: 0 0 8px;
      font-size: 1.45rem;
    }

    .price-card p {
      margin: 0;
      color: var(--muted);
    }

    .price-big {
      font-size: 2.7rem;
      line-height: 1;
      font-weight: 800;
      white-space: nowrap;
    }

    .steps-grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0,1fr));
      gap: 17px;
    }

    .step-card {
      padding: 21px;
      border: 1px solid var(--border);
      border-radius: var(--radius);
      background: rgba(255,255,255,.035);
    }

    .step-number {
      display: grid;
      place-items: center;
      width: 38px;
      height: 38px;
      margin-bottom: 12px;
      border-radius: 50%;
      background: linear-gradient(135deg, var(--accent), var(--accent-light));
      color: #151515;
      font-weight: 800;
    }

    .step-card h3 {
      margin: 0 0 6px;
    }

    .step-card p {
      margin: 0;
      color: var(--muted);
    }

    .contact-box {
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 20px;
      flex-wrap: wrap;
      padding: 27px;
      border: 1px solid var(--border);
      border-radius: 26px;
      background: rgba(255,255,255,.04);
    }

    .contact-box h2 {
      margin-bottom: 7px;
    }

    .contact-box p {
      margin: 0;
      color: var(--muted);
    }

    .footer {
      padding: 24px 0 36px;
      margin-top: 22px;
      border-top: 1px solid var(--border);
      color: var(--muted);
      text-align: center;
      font-size: .9rem;
    }

    .whatsapp-float {
      position: fixed;
      right: 18px;
      bottom: 18px;
      z-index: 30;
      display: grid;
      place-items: center;
      width: 58px;
      height: 58px;
      border-radius: 50%;
      background: var(--green);
      color: #fff;
      font-size: 1.65rem;
      box-shadow: var(--shadow);
    }

    body[dir="rtl"] .whatsapp-float {
      right: auto;
      left: 18px;
    }

    @media (max-width: 850px) {
      .hero-grid {
        grid-template-columns: 1fr;
      }

      .hero-image {
        height: 360px;
      }

      .services-grid,
      .gallery-grid,
      .steps-grid {
        grid-template-columns: repeat(2, minmax(0, 1fr));
      }
    }

    @media (max-width: 600px) {
      .nav {
        padding: 12px 0;
        flex-wrap: wrap;
      }

      .nav-links {
        order: 3;
        width: 100%;
        justify-content: center;
        gap: 15px;
      }

      .languages {
        margin-left: auto;
      }

      body[dir="rtl"] .languages {
        margin-left: 0;
        margin-right: auto;
      }

      .hero {
        padding-top: 48px;
      }

      .hero-image {
        height: 300px;
      }

      .services-grid,
      .gallery-grid,
      .steps-grid {
        grid-template }

      .button {
        width: 100%;
      }

      .contact-box {
        align-items: stretch;
      }
    }
  </style>
</head>

<body>
  <header class="header">
    <div class="container nav">
      <a class="logo" href="#home" aria-label="MohaPhoto">
        <span>Moha</span>Photo
      </a>

      <nav class="nav-links" aria-label="Main navigation">
        <a href="#services" data-i18n="navServices">Servicios</a>
        <a href="#portfolio" data-i18n="navPortfolio">Portafolio</a>
        <a href="#price" data-i18n="navPrice">Precio</a>
        <a href="#contact" data-i18n="navContact">Contacto</a>
      </nav>

      <div class="languages" aria-label="Choose language">
        <button class="language-button active" type="button" data-lang="es">ES</button>
        <button class="language-button" type="button" data-lang="en">EN</button>
        <button class="language-button" type="button" data-lang="ar">عربي</button>
      </div>
    </div>
  </header>

  <main>
    <section class="hero" id="home">
      <div class="container hero-grid">
        <div>
          <div class="eyebrow" data-i18n="eyebrow">Edición de fotos y diseño</div>

          <h1 data-i18n="heroTitle">
            Tus ideas, convertidas en
            <span class="gradient-text">diseños increíbles</span>
          </h1>

          <p class="hero-text" data-i18n="heroText">
            Edición profesional de imágenes y diseño gráfico personalizado para tus fotos, productos, redes sociales y proyectos.
          </p>

          <div class="button-row">
            <a class="button button-primary whatsapp-link"
               href="https://wa.me/34666784846"
               target="_blank" rel="noopener noreferrer"
               data-i18n="heroButton">Pedir por WhatsApp</a>

            <a class="button button-outline" href="#services" data-i18n="servicesButton">
              Ver servicios
            </a>
          </div>

          <div class="price-note">
            <span data-i18n="fixedPrice">Precio fijo</span>
            <strong>100€</strong>
            <span data-i18n="perService">por servicio</span>
          </div>
        </div>

        <div class="hero-image-wrap">
          <img
            class="hero-image"
            src="https://images.unsplash.com/photo-1499951360447-b19be8fe80f5?auto=format&fit=crop&w=1000&q=85"
            alt="Espacio creativo de diseño"
          >
          <div class="image-label" data-i18n="imageLabel">Diseño creativo para tus ideas</div>
        </div>
      </div>
    </section>

    <section id="services">
      <div class="container">
        <div class="section-heading">
          <h2 data-i18n="servicesTitle">Nuestros servicios</h2>
          <p class="section-description" data-i18n="servicesDescription">
            Servicios de edición y diseño para dar a tus imágenes un acabado cuidado y profesional.
          </p>
        </div>

        <div class="services-grid">
          <article class="service-card">
            <div class="service-icon">✦</div>
            <h3 data-i18n="service1Title">Retoque fotográfico</h3>
            <p data-i18n="service1Text">Mejora de luz, color y detalles para que tus fotos tengan un acabado limpio y atractivo.</p>
          </article>

          <article class="service-card">
            <div class="service-icon">◉</div>
            <h3 data-i18n="service2Title">Eliminar o cambiar fondos</h3>
            <p data-i18n="service2Text">Quitamos el fondo o lo cambiamos para adaptar la imagen a tu idea o proyecto.</p>
          </article>

          <article class="service-card">
            <div class="service-icon">✧</div>
            <h3 data-i18n="service3Title">Diseño de logotipos</h3>
            <p data-i18n="service3Text">Diseño visual personalizado para marcas, pequeños negocios y proyectos.</p>
          </article>

          <article class="service-card">
            <div class="service-icon">▣</div>
            <h3 data-i18n="service4Title">Restaurar fotos antiguas</h3>
            <p data-i18n="service4Text">Mejoramos fotografías antiguas y recuperamos detalles cuando la imagen lo permite.</p>
          </article>

          <article class="service-card">
            <div class="service-icon">◌</div>
            <h3 data-i18n="service5Title">Diseño para redes sociales</h3>
            <p data-i18n="service5Text">Publicaciones, historias, portadas y gráficos para presentar tus ideas online.</p>
          </article>

          <article class="service-card">
            <div class="service-icon">✹</div>
            <h3 data-i18n="service6Title">Carteles, flyers y más</h3>
            <p data-i18n="service6Text">Diseños para promociones, eventos, invitaciones, productos y otras necesidades.</p>
          </article>
        </div>
      </div>
    </section>

    <section id="portfolio">
      <div class="container">
        <div class="section-heading">
          <h2 data-i18n="portfolioTitle">Galería de inspiración</h2>
          <p class="section-description" data-i18n="portfolioDescription">
            Estas imágenes son ejemplos visuales. Puedes sustituirlas por tus propios trabajos.
          </p>
        </div>

        <div class="gallery-grid">
          <article class="gallery-card">
            <img
              src="https://images.unsplash.com/photo-1534528741775-53994a69daeb?auto=format&fit=crop&w=800&q=85"
              alt="Retrato para ejemplo de retoque"
              loading="lazy"
            >
            <div class="gallery-caption">
              <h3 data-i18n="gallery1Title">Retoque de retrato</h3>
              <p data-i18n="gallery1Text">Mejora de luz, color y acabado visual.</p>
            </div>
          </article>

          <article class="gallery-card">
            <img
              src="https://images.unsplash.com/photo-1542291026-7eec264c27ff?auto=format&fit=crop&w=800&q=85"
              alt="Producto para ejemplo de diseño"
              loading="lazy"
            >
            <div class="gallery-caption">
              <h3 data-i18n="gallery2Title">Imagen de producto</h3>
              <p data-i18n="gallery2Text">Presentación clara para productos y anuncios.</p>
            </div>
          </article>

          <article class="gallery-card">
            <img
              src="https://images.unsplash.com/photo-1558655146-9f40138edfeb?auto=format&fit=crop&w=800&q=85"
              alt="Ejemplo de diseño gráfico"
              loading="lazy"
            >
            <div class="gallery-caption">
              <h3 data-i18n="gallery3Title">Diseño gráfico</h3>
              <p data-i18n="gallery3Text">Una idea visual para tu marca o proyecto.</p>
            </div>
          </article>
        </div>
      </div>
    </section>

    <section id="price">
      <div class="container">
        <div class="price-card">
          <div>
            <h3 data-i18n="priceTitle">Precio sencillo y claro</h3>
            <p data-i18n="priceDescription">El precio es de 100€ por servicio. Escríbenos para explicar qué necesitas y confirmar los detalles antes de empezar.</p>
          </div>
          <div class="price-big">100€</div>
        </div>
      </div>
    </section>

    <section>
      <div class="container">
        <div class="section-heading">
          <h2 data-i18n="stepsTitle">Cómo funciona</h2>
        </div>

        <div class="steps-grid">
          <article class="step-card">
            <div class="step-number">1</div>
            <h3 data-i18n="step1Title">Cuéntanos tu idea</h3>
            <p data-i18n="step1Text">Escríbenos por WhatsApp y explícanos el servicio que necesitas.</p>
          </article>

          <article class="step-card">
            <div class="step-number">2</div>
            <h3 data-i18n="step2Title">Envía las imágenes</h3>
            <p data-i18n="step2Text">Comparte las fotos y las indicaciones importantes para el diseño.</p>
          </article>

          <article class="step-card">
            <div class="step-number">3</div>
            <h3 data-i18n="step3Title">Recibe tu diseño</h3>
            <p data-i18n="step3Text">Preparamos el trabajo y hablamos contigo sobre los ajustes necesarios.</p>
          </article>
        </div>
      </div>
    </section>

    <section id="contact">
      <div class="container">
        <div class="contact-box">
          <div>
            <h2 data-i18n="contactTitle">¿Empezamos con tu proyecto?</h2>
            <p data-i18n="contactText">Escríbenos por WhatsApp para consultar o pedir un servicio.</p>
          </div>

          <a class="button button-primary whatsapp-link"
             href="https://wa.me/34666784846"
             target="_blank" rel="noopener noreferrer"
             data-i18n="contactButton">WhatsApp: +34 666 784 846</a>
        </div>
      </div>
    </section>
  </main>

  <a class="whatsapp-float whatsapp-link"
     href="https://wa.me/34666784846"
     target="_blank" rel="noopener noreferrer"
     aria-label="WhatsApp">✆</a>

  <footer class="footer">
    <div class="container">
      © 2026 MohaPhoto — <span data-i18n="footerText">Edición de fotos y diseño gráfico</span>
    </div>
  </footer>

  <script>
    const translations = {
      es: {
        navServices: "Servicios",
        navPortfolio: "Portafolio",
        navPrice: "Precio",
        navContact: "Contacto",
        eyebrow: "Edición de fotos y diseño",
        heroTitle: "Tus ideas, convertidas en <span class='gradient-text'>diseños increíbles</span>",
        heroText: "Edición profesional de imágenes y diseño gráfico personalizado para tus fotos, productos, redes sociales y proyectos.",
        heroButton: "Pedir por WhatsApp",
        servicesButton: "Ver servicios",
        fixedPrice: "Precio fijo",
        perService: "por servicio",
        imageLabel: "Diseño creativo para tus ideas",
        servicesTitle: "Nuestros servicios",
        servicesDescription: "Servicios de edición y diseño para dar a tus imágenes un acabado cuidado y profesional.",
        service1Title: "Retoque fotográfico",
        service1Text: "Mejora de luz, color y detalles para que tus fotos tengan un acabado limpio y atractivo.",
        service2Title: "Eliminar o cambiar fondos",
        service2Text: "Quitamos el fondo o lo cambiamos para adaptar la imagen a tu idea o proyecto.",
        service3Title: "Diseño de logotipos",
        service3Text: "Diseño visual personalizado para marcas, pequeños negocios y proyectos.",
        service4Title: "Restaurar fotos antiguas",
        service4Text: "Mejoramos fotografías antiguas y recuperamos detalles cuando la imagen lo permite.",
        service5Title: "Diseño para redes sociales",
        service5Text: "Publicaciones, historias, portadas y gráficos para presentar tus ideas online.",
        service6Title: "Carteles, flyers y más",
        service6Text: "Diseños para promociones, eventos, invitaciones, productos y otras necesidades.",
        portfolioTitle: "Galería de inspiración",
        portfolioDescription: "Estas imágenes son ejemplos visuales. Puedes sustituirlas por tus propios trabajos.",
        gallery1Title: "Retoque de retrato",
        gallery1Text: "Mejora de luz, color y acabado visual.",
        gallery2Title: "Imagen de producto",
        gallery2Text: "Presentación clara para productos y anuncios.",
        gallery3Title: "Diseño gráfico",
        gallery3Text: "Una idea visual para tu marca o proyecto.",
        priceTitle: "Precio sencillo y claro",
        priceDescription: "El precio es de 100€ por servicio. Escríbenos para explicar qué necesitas y confirmar los detalles antes de empezar.",
        stepsTitle: "Cómo funciona",
        step1Title: "Cuéntanos tu idea",
        step1Text: "Escríbenos por WhatsApp y explícanos el servicio que necesitas.",
        step2Title: "Envía las imágenes",
        step2Text: "Comparte las fotos y las indicaciones importantes para el diseño.",
        step3Title: "Recibe tu diseño",
        step3Text: "Preparamos el trabajo y hablamos contigo sobre los ajustes necesarios.",
        contactTitle: "¿Empezamos con tu proyecto?",
        contactText: "Escríbenos por WhatsApp para consultar o pedir un servicio.",
        contactButton: "WhatsApp: +34 666 784 846",
        footerText: "Edición de fotos y diseño gráfico"
      },

      en: {
        navServices: "Services",
        navPortfolio: "Portfolio",
        navPrice: "Pricing",
        navContact: "Contact",
        eyebrow: "Photo editing and design",
        heroTitle: "Your ideas, turned into <span class='gradient-text'>amazing designs</span>",
        heroText: "Professional photo editing and custom graphic design for your photos, products, social media and projects.",
        heroButton: "Order on WhatsApp",
        servicesButton: "View services",
        fixedPrice: "Fixed price",
        perService: "per service",
        imageLabel: "Creative design for your ideas",
        servicesTitle: "Our services",
        servicesDescription: "Editing and design services to give your images a polished, professional finish.",
        service1Title: "Photo retouching",
        service1Text: "Improve lighting, color and details for a clean, attractive finish.",
        service2Title: "Background removal or replacement",
        service2Text: "Remove or replace the background to match your idea or project.",
        service3Title: "Logo design",
        service3Text: "Custom visual design for brands, small businesses and projects.",
        service4Title: "Old photo restoration",
        service4Text: "Improve old photographs and recover details where the image allows.",
        service5Title: "Social media design",
        service5Text: "Posts, stories, covers and graphics to present your ideas online.",
        service6Title: "Posters, flyers and more",
        service6Text: "Designs for promotions, events, invitations, products and other needs.",
        portfolioTitle: "Inspiration gallery",
        portfolioDescription: "These are sample images. You can replace them with your own work.",
        gallery1Title: "Portrait retouching",
        gallery1Text: "Improved lighting, color and visual finish.",
        gallery2Title: "Product image",
        gallery2Text: "Clear presentation for products and advertisements.",
        gallery3Title: "Graphic design",
        gallery3Text: "A visual idea for your brand or project.",
        priceTitle: "Simple, clear pricing",
        priceDescription: "The price is €100 per service. Contact us to explain what you need and confirm the details before work begins.",
        stepsTitle: "How it works",
        step1Title: "Tell us your idea",
        step1Text: "Message us on WhatsApp and explain which service you need.",
        step2Title: "Send your images",
        step2Text: "Share your photos and any important design instructions.",
        step3Title: "Receive your design",
        step3Text: "We prepare the work and discuss any needed adjustments with you.",
        contactTitle: "Ready to start your project?",
        contactText: "Message us on WhatsApp to ask a question or order a service.",
        contactButton: "WhatsApp: +34 666 784 846",
        footerText: "Photo editing and graphic design"
      },

      ar: {
        navServices: "الخدمات",
        navPortfolio: "معرض الأعمال",
        navPrice: "السعر",
        navContact: "التواصل",
        eyebrow: "تعديل الصور والتصميم",
        heroTitle: "أفكارك تتحول إلى <span class='gradient-text'>تصاميم مميزة</span>",
        heroText: "تعديل احترافي للصور وتصميم جرافيكي حسب الطلب لصورك ومنتجاتك ومواقع التواصل ومشاريعك.",
        heroButton: "اطلب عبر واتساب",
        servicesButton: "شاهد الخدمات",
        fixedPrice: "السعر الثابت",
        perService: "لكل خدمة",
        imageLabel: "تصميم إبداعي لأفكارك",
        servicesTitle: "خدماتنا",
        servicesDescription: "خدمات تعديل وتصميم تمنح صورك مظهراً أنيقاً واحترافياً.",
        service1Title: "تعديل الصور",
        service1Text: "تحسين الإضاءة والألوان والتفاصيل للحصول على نتيجة جذابة ومرتبة.",
        service2Title: "إزالة الخلفية أو تغييرها",
        service2Text: "نزيل الخلفية أو نغيرها لتناسب فكرتك أو مشروعك.",
        service3Title: "تصميم الشعارات",
        service3Text: "تصميم بصري مخصص للعلامات التجارية والأعمال والمشاريع.",
        service4Title: "ترميم الصور القديمة",
        service4Text: "تحسين الصور القديمة واستعادة تفاصيلها عندما تسمح جودة الصورة بذلك.",
        service5Title: "تصاميم مواقع التواصل",
        service5Text: "منشورات وقصص وأغلفة وتصاميم لعرض أفكارك على الإنترنت.",
        service6Title: "ملصقات ومنشورات وغيرها",
        service6Text: "تصاميم للعروض والفعاليات والدعوات والمنتجات واحتياجات أخرى.",
        portfolioTitle: "معرض للإلهام",
        portfolioDescription: "هذه صور تجريبية. يمكنك استبدالها بأعمالك الخاصة.",
        gallery1Title: "تعديل الصور الشخصية",
        gallery1Text: "تحسين الإضاءة والألوان والمظهر العام.",
        gallery2Title: "صور المنتجات",
        gallery2Text: "عرض واضح للمنتجات والإعلانات.",
        gallery3Title: "التصميم الجرافيكي",
        gallery3Text: "فكرة بصرية لعلامتك التجارية أو مشروعك.",
        priceTitle: "سعر واضح وبسيط",
        priceDescription: "السعر 100€ لكل خدمة. تواصل معنا واشرح ما تحتاجه لتأكيد التفاصيل قبل بدء العمل.",
        stepsTitle: "طريقة العمل",
        step1Title: "اشرح فكرتك",
        step1Text: "راسلنا عبر واتساب واشرح الخدمة التي تحتاج إليها.",
        step2Title: "أرسل الصور",
        step2Text: "أرسل صورك وأي تعليمات مهمة خاصة بالتصميم.",
        step3Title: "استلم التصميم",
        step3Text: "نجهز العمل ونتواصل معك بخصوص أي تعديلات لازمة.",
        contactTitle: "هل نبدأ مشروعك؟",
        contactText: "راسلنا عبر واتساب للاستفسار أو لطلب خدمة.",
        contactButton: "واتساب: +34 666 784 846",
        footerText: "تعديل الصور والتصميم الجرافيكي"
      }
    };

    function setLanguage(language) {
      const languageData = translations[language];
      if (!languageData) return;

      document.documentElement.lang = language;
      document.documentElement.dir = language === "ar" ? "rtl" : "ltr";
      document.body.dir = language === "ar" ? "rtl" : "ltr";

      document.querySelectorAll("[data-i18n]").forEach((element) => {
        const key = element.dataset.i18n;
        if (languageData[key]) {
          element.innerHTML = languageData[key];
        }
      });

      document.querySelectorAll(".language-button").forEach((button) => {
        button.classList.toggle("active", button.dataset.lang === language);
      });

      try {
        localStorage.setItem("mohaphoto-language", language);
      } catch (error) {
        // Language selection still works if browser storage is unavailable.
      }
    }

    document.querySelectorAll(".language-button").forEach((button) => {
      button.addEventListener("click", () => {
        setLanguage(button.dataset.lang);
      });
    });

    let savedLanguage = "es";
    try {
      savedLanguage = localStorage.getItem("mohaphoto-language") || "es";
    } catch (error) {
      savedLanguage = "es";
    }

    setLanguage(savedLanguage);
  </script>
</body>
</html>
```**مهم:** صور المعرض الموجودة أمثلة من الإنترنت، بدّلها بصور أعمالك قبل نشر الموقع. Aamma-final
