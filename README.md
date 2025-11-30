<!DOCTYPE html>
<html lang="uz">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>NEUROBANK OS — Self-Driving Bank Intelligence</title>
  <style>
    :root {
      --bg: #050816;
      --card: #0b1020;
      --accent: #4f46e5;
      --accent-soft: rgba(79,70,229,0.25);
      --text-main: #f9fafb;
      --text-muted: #9ca3af;
      --border-subtle: rgba(148,163,184,0.3);
    }
    * { box-sizing: border-box; }
    body {
      margin: 0;
      font-family: system-ui, -apple-system, BlinkMacSystemFont, "SF Pro", Arial, sans-serif;
      background: radial-gradient(circle at top, #111827 0, #020617 45%, #020617 100%);
      color: var(--text-main);
    }
    a { color: #93c5fd; text-decoration: none; }

    /* HEADER */
    header {
      padding: 40px 16px 50px;
      position: relative;
      overflow: hidden;
    }
    .hero-inner {
      max-width: 1040px;
      margin: 0 auto;
      position: relative;
      z-index: 2;
      text-align: left;
    }
    .hero-badge {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      padding: 4px 10px;
      border-radius: 999px;
      background: rgba(15,23,42,0.8);
      border: 1px solid rgba(148,163,184,0.4);
      font-size: 12px;
      color: var(--text-muted);
      margin-bottom: 14px;
    }
    .hero-badge-dot {
      width: 7px;
      height: 7px;
      border-radius: 999px;
      background: #22c55e;
      box-shadow: 0 0 12px rgba(34,197,94,0.9);
    }
    h1 {
      font-size: clamp(32px, 4vw, 40px);
      margin: 0 0 10px;
      letter-spacing: 0.03em;
    }
    .hero-gradient {
      background: linear-gradient(120deg,#e5e7eb,#a5b4fc,#38bdf8);
      -webkit-background-clip: text;
      color: transparent;
    }
    .hero-sub {
      max-width: 560px;
      color: var(--text-muted);
      font-size: 14px;
      line-height: 1.7;
    }
    .hero-grid {
      margin-top: 26px;
      display: grid;
      gap: 18px;
      grid-template-columns: 2.2fr 1.3fr;
    }
    @media (max-width: 900px) {
      .hero-grid { grid-template-columns: 1fr; }
    }
    .hero-metrics {
      display: grid;
      grid-template-columns: repeat(3, minmax(0,1fr));
      gap: 10px;
      margin-top: 10px;
    }
    .metric {
      padding: 10px 10px 12px;
      border-radius: 12px;
      background: radial-gradient(circle at top,rgba(79,70,229,0.26),rgba(15,23,42,0.9));
      border: 1px solid rgba(129,140,248,0.5);
    }
    .metric-label {
      font-size: 11px;
      color: var(--text-muted);
    }
    .metric-value {
      font-size: 17px;
      font-weight: 600;
      margin-top: 3px;
    }
    .metric-sub {
      font-size: 11px;
      color: #9ca3af;
      margin-top: 2px;
    }
    .hero-scenario {
      background: linear-gradient(145deg,rgba(15,23,42,0.95),rgba(30,64,175,0.9));
      border-radius: 16px;
      padding: 14px 14px 14px;
      border: 1px solid rgba(129,140,248,0.5);
      box-shadow: 0 0 40px rgba(37,99,235,0.35);
      font-size: 12px;
      line-height: 1.6;
    }
    .scenario-tag {
      display:inline-flex;
      align-items:center;
      gap:6px;
      font-size:11px;
      color:#bfdbfe;
      margin-bottom: 4px;
    }
    .scenario-tag-dot {
      width:6px;
      height:6px;
      border-radius:999px;
      background:#facc15;
    }
    .hero-background-orbit {
      position: absolute;
      inset: -200px -120px auto auto;
      background: radial-gradient(circle at top,#1d4ed8 0, transparent 55%);
      opacity: 0.4;
      filter: blur(12px);
      z-index: 1;
    }

    /* SECTIONS */
    main {
      padding: 0 16px 40px;
    }
    .section {
      max-width: 1040px;
      margin: 0 auto 24px;
    }
    .section-title {
      font-size: 17px;
      margin-bottom: 10px;
      display:flex;
      align-items:center;
      gap:8px;
    }
    .section-chip {
      font-size: 11px;
      padding: 2px 8px;
      border-radius: 999px;
      border: 1px solid rgba(148,163,184,0.6);
      color: var(--text-muted);
    }

    .card {
      background: radial-gradient(circle at top left,rgba(15,118,110,0.06),rgba(15,23,42,0.98));
      border-radius: 16px;
      padding: 18px 18px 18px;
      border: 1px solid var(--border-subtle);
      box-shadow: 0 18px 45px rgba(15,23,42,0.9);
      font-size: 13px;
      color: var(--text-muted);
      line-height: 1.7;
    }
    .card h3 {
      margin-top: 0;
      margin-bottom: 6px;
      font-size: 15px;
      color: var(--text-main);
    }
    ul { padding-left: 18px; }
    li { margin-bottom: 4px; }

    .two-col {
      display:grid;
      grid-template-columns: minmax(0,1.3fr) minmax(0,1fr);
      gap:16px;
    }
    @media (max-width: 900px) {
      .two-col { grid-template-columns: 1fr; }
    }

    /* Roadmap */
    .roadmap-grid {
      display:grid;
      grid-template-columns: repeat(4,minmax(0,1fr));
      gap:10px;
    }
    @media (max-width: 900px) {
      .roadmap-grid { grid-template-columns: 1fr 1fr; }
    }
    @media (max-width: 640px) {
      .roadmap-grid { grid-template-columns: 1fr; }
    }
    .roadmap-step {
      border-radius: 14px;
      padding: 12px 12px 13px;
      background: linear-gradient(145deg,rgba(30,64,175,0.18),rgba(15,23,42,0.98));
      border: 1px solid rgba(129,140,248,0.6);
    }
    .roadmap-step-label {
      font-size: 11px;
      text-transform: uppercase;
      letter-spacing: 0.08em;
      color: #a5b4fc;
      margin-bottom: 4px;
    }
    .roadmap-step-title {
      font-size: 13px;
      font-weight: 600;
      color: var(--text-main);
      margin-bottom: 4px;
    }
    .roadmap-step ul { font-size: 12px; }

    /* Chips / tags list */
    .tag-row {
      display:flex;
      flex-wrap:wrap;
      gap:6px;
      margin-top:6px;
    }
    .tag {
      font-size: 11px;
      padding: 3px 8px;
      border-radius: 999px;
      background: rgba(15,23,42,0.9);
      border: 1px solid rgba(55,65,81,0.9);
      color: #e5e7eb;
    }

    .footer-note {
      max-width:1040px;
      margin:22px auto 0;
      font-size:11px;
      color:#6b7280;
      text-align:right;
    }
  </style>
</head>
<body>

<header>
  <div class="hero-background-orbit"></div>

  <div class="hero-inner">
    <div class="hero-badge">
      <div class="hero-badge-dot"></div>
      <span>AI500 Demo · Bank uchun AI Operating System</span>
    </div>

    <h1>
      <span class="hero-gradient">NEUROBANK OS</span><br>
      <span style="font-size:0.82em; font-weight:400; color:#e5e7eb;">Self-Driving Bank Intelligence Layer</span>
    </h1>

    <div class="hero-grid">
      <div>
        <p class="hero-sub">
          NEUROBANK OS — bu mavjud bank tizimlari ustida ishlaydigan “miya”.
          U kreditlar, fraud, narxlash va mijozlar bilan muloqotni real vaqt rejimida
          boshqaradigan AGI-ga yaqin multi-agent tizim.
        </p>

        <div class="hero-metrics">
          <div class="metric">
            <div class="metric-label">Kredit qarorlari</div>
            <div class="metric-value">x15 tezroq</div>
            <div class="metric-sub">real-time AI skoring</div>
          </div>
          <div class="metric">
            <div class="metric-label">Fraud yo‘qotishlari</div>
            <div class="metric-value">−30%</div>
            <div class="metric-sub">proaktiv monitoring</div>
          </div>
          <div class="metric">
            <div class="metric-label">Mijozlar qoniqishi</div>
            <div class="metric-value">+25%</div>
            <div class="metric-sub">24/7 AI-bankir</div>
          </div>
        </div>
      </div>

      <div class="hero-scenario">
        <div class="scenario-tag">
          <span class="scenario-tag-dot"></span>
          <span>LIVE SCENARIO · 2 soniyada qaror</span>
        </div>
        <p>
          27 yoshli mijoz mobil ilovada 80 mln so‘mlik iste’mol krediti so‘raydi.
          NEUROBANK OS bir vaqtning o‘zida:
        </p>
        <ul>
          <li>tranzaksiyalar tarixini va boshqa banklardagi ma’lumotlarni vektor bazadan tortib oladi;</li>
          <li>3 xil ML modeli va 1 LLM orqali riskni baholaydi;</li>
          <li>fraud-agent so‘nggi 30 kunlik g‘ayrioddiy xatti-harakatlarni tekshiradi;</li>
          <li>AI-bankir esa mijozga tushunarli tilda “Nega aynan shunday qaror chiqdi?” deb izoh beradi.</li>
        </ul>
        <p style="margin-top:4px;">Natija: 2 soniyada tushunarli, izohli va auditga tayyor qaror.</p>
      </div>
    </div>
  </div>
</header>

<main>

  <!-- 1. Muammo → Yechim -->
  <section class="section">
    <div class="section-title">
      <span>1. Muammo → Yechim</span>
      <span class="section-chip">Core problem & vision</span>
    </div>
    <div class="card two-col">
      <div>
        <h3>Bugungi banklarning og‘riqli nuqtalari</h3>
        <ul>
          <li><b>Qo‘lda kredit baholash:</b> subyektiv, sekin va inson xatosiga ochiq.</li>
          <li><b>Fraud kech aniqlanadi:</b> tranzaksiyalar ko‘pi offline tahlil qilinadi.</li>
          <li><b>Fragmentatsiya:</b> kredit, CRM, call-center, scoring tizimlari bir-biridan uzilgan.</li>
          <li><b>Regulyator talablari:</b> “Nega bu qaror qabul qilindi?” savoliga AI darajasida izoh berish qiyin.</li>
        </ul>
      </div>
      <div>
        <h3>Yechim: NEUROBANK OS</h3>
        <ul>
          <li><b>Self-driving qatlam:</b> mavjud core banking ustida ishlaydigan AI “operatsion tizim”.</li>
          <li><b>Multi-agent arxitektura:</b> Credit Agent, Fraud Agent, Pricing Agent, CX Agent birgalikda ishlaydi.</li>
          <li><b>Explainable AI:</b> har bir qaror uchun inson tushunadigan izoh va risk kartasi yaratadi.</li>
          <li><b>Real-time loop:</b> tranzaksiyalar, bozor sharoiti va mijoz xatti-harakati asosida modellari doimiy yangilanadi.</li>
        </ul>
      </div>
    </div>
  </section>

  <!-- 2. Jamoa -->
  <section class="section">
    <div class="section-title">
      <span>2. Jamoa (rollar, ko‘nikmalar, texnologiyalar staki)</span>
      <span class="section-chip">Team & tech</span>
    </div>
    <div class="card">
      <h3>Jamoa rollari</h3>
      <ul>
        <li>
          <b>Rahimjon — Lead AI Engineer & Product Owner</b><br>
          Ko‘nikmalar: LLM agentlar, kredit/fraud modellari, MLOps, prompt engineering.<br>
          Tech: Python, PyTorch, LangChain, OpenAI / Claude / Gemini API, vector DB (Qdrant / Weaviate).
        </li>
        <li>
          <b>Backend Engineer</b><br>
          Ko‘nikmalar: yuqori yuklama uchun API dizayni, mikroservislar, security.<br>
          Tech: FastAPI, gRPC, PostgreSQL, Redis, Kafka, Docker, Kubernetes.
        </li>
        <li>
          <b>Frontend Engineer</b><br>
          Ko‘nikmalar: real-time monitoring dashboard, risk panel UI, explainability vizualizatsiyasi.<br>
          Tech: React, Next.js, Tailwind CSS, TypeScript.
        </li>
        <li>
          <b>Risk & Compliance Analyst</b><br>
          Ko‘nikmalar: bank risk siyosati, AML/KYC, regulyator talablari, model validation.
        </li>
      </ul>

      <h3>Texnologiyalar staki</h3>
      <div class="tag-row">
        <span class="tag">Python / FastAPI</span>
        <span class="tag">React / Next.js</span>
        <span class="tag">PostgreSQL</span>
        <span class="tag">Kafka / Event streaming</span>
        <span class="tag">Vector DB (Qdrant / Weaviate)</span>
        <span class="tag">OpenAI · Claude · Gemini · Llama</span>
        <span class="tag">Docker / K8s</span>
        <span class="tag">Prometheus / Grafana</span>
      </div>
    </div>
  </section>

  <!-- 3. Nima uchun aynan biz? -->
  <section class="section">
    <div class="section-title">
      <span>3. Nima uchun jamoamiz bu muammoni hal qila oladi?</span>
      <span class="section-chip">Unfair advantage</span>
    </div>
    <div class="card two-col">
      <div>
        <h3>Texnik ustunligimiz</h3>
        <ul>
          <li>LLM-agentlar va klassik ML modellarini <b>bir ekotizimda birlashtirish</b> bo‘yicha tajriba.</li>
          <li>AI-ga tushunarli bo‘lgan, lekin regulyator uchun ham <b>izohli va auditga tayyor</b> arxitektura.</li>
          <li>Real-time streaming (Kafka) va batch tahlilni kombinatsiya qilish.</li>
        </ul>
      </div>
      <div>
        <h3>Bozor va domen tushunchasi</h3>
        <ul>
          <li>Markaziy Osiyodagi banklarning real og‘riqli nuqtalari: navbatlar, sekin kredit, fraud.</li>
          <li>Mahalliy regulatsiya va compliance talablarini inobatga olgan dizayn.</li>
          <li>Bank uchun “AGI-ga yaqin” yechimni <b>real biznes KPI</b> bilan bog‘lab berish: NPL, LTV, CAC.</li>
        </ul>
      </div>
    </div>
  </section>

  <!-- 4. Yo‘l xaritasi -->
  <section class="section">
    <div class="section-title">
      <span>4. Yo‘l xaritasi: Idea / Prototype / MVP / Launched</span>
      <span class="section-chip">Timeline</span>
    </div>
    <div class="card">
      <div class="roadmap-grid">
        <div class="roadmap-step">
          <div class="roadmap-step-label">Stage 1</div>
          <div class="roadmap-step-title">Idea (bugun)</div>
          <ul>
            <li>NEUROBANK OS konsepsiyasi va arxitekturasi.</li>
            <li>Asosiy agentlar: Credit, Fraud, CX, Pricing.</li>
            <li>Bank core’dan mustaqil, lekin integratsiyaga tayyor qatlam sifatida dizayn.</li>
          </ul>
        </div>
        <div class="roadmap-step">
          <div class="roadmap-step-label">Stage 2</div>
          <div class="roadmap-step-title">Prototype (3–4 hafta)</div>
          <ul>
            <li>Demo-bank data (sintetik + anonimlashtirilgan) bilan ishlaydigan prototip.</li>
            <li>Credit Agent uchun birinchi skoring modeli + LLM izoh generatori.</li>
            <li>Web-dashboard: “AI qarori + izohi + risk kartasi”.</li>
          </ul>
        </div>
        <div class="roadmap-step">
          <div class="roadmap-step-label">Stage 3</div>
          <div class="roadmap-step-title">MVP (3 oy)</div>
          <ul>
            <li>Real bank sandbox API’lari bilan integratsiya.</li>
            <li>Fraud Agent va Pricing Agent ishga tushishi.</li>
            <li>Monitoring, alerting va basic MLOps pipeline.</li>
          </ul>
        </div>
        <div class="roadmap-step">
          <div class="roadmap-step-label">Stage 4</div>
          <div class="roadmap-step-title">Launched (pilot)</div>
          <ul>
            <li>1-bank bilan pilot: 1–2 mahsulot (iste’mol krediti / karta).</li>
            <li>KPI: qaror berish tezligi, default rate, fraud loss, NPS.</li>
            <li>SaaS / RevShare modeli va multi-bank qo‘llab-quvvatlash.</li>
          </ul>
        </div>
      </div>
    </div>
  </section>

  <!-- 5. Amalga oshirish rejasi -->
  <section class="section">
    <div class="section-title">
      <span>5. Yechimni qanday amalga oshiramiz?</span>
      <span class="section-chip">Architecture & AI tools</span>
    </div>
    <div class="card two-col">
      <div>
        <h3>Arxitektura (yuqori darajadagi ko‘rinish)</h3>
        <ul>
          <li><b>Data Layer:</b> core banking, kartalar, CRM, call-center loglari, tashqi byuro ma’lumotlari.</li>
          <li><b>Feature Store:</b> real-time va batch feature’larni saqlovchi qatlam.</li>
          <li><b>Model Layer:</b> kredit skoring, fraud detection, churn prediction, next-best-offer modellari.</li>
          <li><b>LLM Agent Layer:</b> har bir model atrofida “izoh beruvchi” va “qarorni ssenariyga ulovchi” agentlar.</li>
          <li><b>Experience Layer:</b> operator paneli, boshqaruv dashboardi, mijozga ko‘rinadigan AI-bankir.</li>
        </ul>
      </div>
      <div>
        <h3>AI vositalari va texnik detallar</h3>
        <ul>
          <li>LLM router: so‘rov turiga qarab GPT / Claude / Gemini / Llama dan optimalini tanlaydi.</li>
          <li>Vector DB: mijoz tarixini, hujjatlarni, siyosat hujjatlarini semantik qidirish uchun.</li>
          <li>Fraud uchun: gradient boosting + graph-based pattern analitika.</li>
          <li>Explainability: SHAP / LIME + LLM orqali insonga tushunarli matnli izohlar.</li>
          <li>Security & compliance: audit log, rol-based access, PII shifrlash, lokal deployment opsiyasi.</li>
        </ul>
        <p style="margin-top:6px;">
          Maqsad: bankni to‘liq almashtirish emas, balki unga <b>“avtopilot rejimi”</b> qo‘shish —
          strategik qarorlar odamlarda, lekin ma’lumotni qayta ishlash va takliflarni yaratish NEUROBANK OS zimmasida.
        </p>
      </div>
    </div>
  </section>

  <div class="footer-note">
    Demo AI500 1-bosqich uchun tayyorlangan. Kontent namoyish maqsadida yozilgan.
  </div>

</main>

</body>
</html>
