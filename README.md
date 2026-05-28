
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SBESOH — Dashboard One Health SE 22 · 2026</title>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@tabler/icons-webfont@3.3.0/tabler-icons.min.css">
<style>
*{box-sizing:border-box;margin:0;padding:0;}
:root{
  --color-background-primary:#ffffff;
  --color-background-secondary:#f7f8fa;
  --color-background-tertiary:#eef0f4;
  --color-background-info:#e6f1fb;
  --color-border-tertiary:#e2e5ec;
  --color-border-secondary:#c8cdd8;
  --color-text-primary:#1a1d23;
  --color-text-secondary:#6b7280;
  --font-sans:'Inter',system-ui,sans-serif;
  --font-mono:'JetBrains Mono',monospace;
  --border-radius-lg:10px;
  --border-radius-md:6px;
}
body{font-family:var(--font-sans);background:var(--color-background-tertiary);min-height:100vh;}

/* ── MODULE SWITCHER BAR ── */
.module-bar{
  background:#0F1F5C;
  color:#fff;
  display:flex;
  align-items:stretch;
  padding:0;
  position:sticky;
  top:0;
  z-index:1000;
  box-shadow:0 2px 8px rgba(0,0,0,0.18);
}
.module-brand{
  display:flex;
  align-items:center;
  gap:8px;
  padding:9px 16px;
  border-right:1px solid rgba(255,255,255,0.12);
  flex-shrink:0;
}
.module-brand-title{font-size:13px;font-weight:600;letter-spacing:.2px;}
.module-brand-sub{font-size:10px;opacity:.6;}
.badge-oh{background:#C9A84C;color:#0F1F5C;font-size:10px;font-weight:600;padding:2px 7px;border-radius:4px;flex-shrink:0;}
.module-tabs{display:flex;flex:1;overflow-x:auto;}
.module-tab{
  display:flex;
  flex-direction:column;
  align-items:center;
  justify-content:center;
  padding:8px 20px;
  font-size:11px;
  color:rgba(255,255,255,0.65);
  cursor:pointer;
  border-bottom:3px solid transparent;
  border-right:1px solid rgba(255,255,255,0.07);
  white-space:nowrap;
  transition:all .15s;
  gap:3px;
  min-width:130px;
}
.module-tab:hover{background:rgba(255,255,255,0.07);color:#fff;}
.module-tab.active{border-bottom-color:#C9A84C;color:#fff;background:rgba(201,168,76,0.10);}
.module-tab .mt-icon{font-size:16px;opacity:.8;}
.module-tab .mt-label{font-weight:500;font-size:12px;}
.module-tab .mt-sub{font-size:9px;opacity:.6;font-weight:400;}
.module-tab.active .mt-icon,.module-tab.active .mt-sub{opacity:1;}
.module-right{display:flex;align-items:center;gap:10px;padding:0 14px;font-size:11px;opacity:.75;flex-shrink:0;border-left:1px solid rgba(255,255,255,0.12);}
.sdot{width:7px;height:7px;border-radius:50%;background:#4ade80;display:inline-block;margin-right:3px;}
.badge-live{background:#C9A84C;color:#3a2800;font-size:10px;font-weight:500;padding:2px 7px;border-radius:20px;}

/* ── MODULE CONTAINERS ── */
.sbesoh-module{display:none;}
.sbesoh-module.active{display:block;}

/* ── Ensure each module's .app fills properly ── */
.sbesoh-module .app{min-height:calc(100vh - 48px);}
</style>
</head>
<body>

<div class="module-bar">
  <div class="module-brand">
    <span class="badge-oh">ONE HEALTH</span>
    <div>
      <div class="module-brand-title">SBESOH</div>
      <div class="module-brand-sub">SE 22 · Madagascar · FHI360/STRIDES</div>
    </div>
  </div>
  <div class="module-tabs">
    <div class="module-tab active" onclick="switchModule('v3')">
      <span class="mt-icon"><i class="ti ti-virus"></i></span>
      <span class="mt-label">SIMR Surveillance</span>
      <span class="mt-sub">Maladies · Tendances · Indicateurs · Alertes</span>
    </div>
    <div class="module-tab" onclick="switchModule('madsur')">
      <span class="mt-icon"><i class="ti ti-pig"></i></span>
      <span class="mt-label">MADSUR Surveillance</span>
      <span class="mt-sub">10 signaux · STREBIAN · Indice Z · Suivi hebdo</span>
    </div>
    <div class="module-tab" onclick="switchModule('carto')">
      <span class="mt-icon"><i class="ti ti-map-2"></i></span>
      <span class="mt-label">Cartographie OH</span>
      <span class="mt-sub">22 régions · SIMR+MADSUR · Alertes</span>
    </div>
    <div class="module-tab" onclick="switchModule('v5')">
      <span class="mt-icon"><i class="ti ti-git-merge"></i></span>
      <span class="mt-label">Intégré One Health</span>
      <span class="mt-sub">SIMR · MADSUR · OH · Top5 · Croisée · Bulletin</span>
    </div>
  </div>
  <div class="module-right">
    <span class="badge-live"><i class="ti ti-circle-filled" style="font-size:8px;margin-right:3px"></i>LIVE</span>
    <span><span class="sdot"></span>Pipeline actif</span>
    <span style="opacity:.5;font-size:10px;">28/05/2026 · SE 22</span>
  </div>
</div>

<div id="module-v3" class="sbesoh-module">

<style>
*{box-sizing:border-box;margin:0;padding:0;}
.app{font-family:var(--font-sans);background:var(--color-background-tertiary);}
.topbar{background:#0F1F5C;color:#fff;padding:9px 16px;display:flex;align-items:center;justify-content:space-between;}
.tb-brand{font-size:13px;font-weight:500;}
.tb-sub{font-size:11px;opacity:.6;}
.badge-oh{background:#C9A84C;color:#0F1F5C;font-size:10px;font-weight:500;padding:2px 7px;border-radius:4px;}
.tb-right{display:flex;align-items:center;gap:12px;font-size:11px;opacity:.8;}
.sdot{width:7px;height:7px;border-radius:50%;background:#4ade80;display:inline-block;margin-right:4px;}
.nav{background:var(--color-background-primary);border-bottom:.5px solid var(--color-border-tertiary);display:flex;gap:0;padding:0 16px;overflow-x:auto;}
.ntab{padding:9px 13px;font-size:12px;cursor:pointer;border-bottom:2px solid transparent;color:var(--color-text-secondary);white-space:nowrap;display:flex;align-items:center;gap:5px;}
.ntab.active{border-bottom-color:#0F1F5C;color:var(--color-text-primary);font-weight:500;}
.ntab:hover:not(.active){color:var(--color-text-primary);background:var(--color-background-secondary);}
.content{padding:14px 16px;}
.card{background:var(--color-background-primary);border:.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-lg);padding:12px 14px;margin-bottom:12px;}
.ct{font-size:12px;font-weight:500;color:var(--color-text-primary);margin-bottom:10px;display:flex;align-items:center;justify-content:space-between;}
.ct-l{display:flex;align-items:center;gap:6px;}
.two{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:12px;}
.three{display:grid;grid-template-columns:1fr 1fr 1fr;gap:10px;margin-bottom:12px;}
.tab-content{display:none;}.tab-content.active{display:block;}
.btn-s{background:var(--color-background-primary);border:.5px solid var(--color-border-secondary);border-radius:var(--border-radius-md);padding:5px 10px;font-size:11px;cursor:pointer;display:flex;align-items:center;gap:4px;color:var(--color-text-primary);}
.btn-s:hover{background:var(--color-background-secondary);}
.btn-p{background:#0F1F5C;color:#fff;border:none;border-radius:var(--border-radius-md);padding:6px 12px;font-size:11px;cursor:pointer;display:flex;align-items:center;gap:4px;}
.krow{display:grid;grid-template-columns:repeat(auto-fit,minmax(110px,1fr));gap:9px;margin-bottom:14px;}
.kpi{background:var(--color-background-primary);border:.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-md);padding:10px 12px;}
.kl{font-size:10px;color:var(--color-text-secondary);margin-bottom:3px;}
.kv{font-size:20px;font-weight:500;line-height:1.1;}
.ks{font-size:10px;color:var(--color-text-secondary);margin-top:2px;}
.up{color:#E65100;}.dn{color:#1B5E20;}
.disease-card{border-radius:var(--border-radius-md);padding:9px 11px;border:.5px solid;}
.filter-row{display:flex;gap:7px;margin-bottom:10px;flex-wrap:wrap;align-items:center;}
.filter-btn{padding:4px 10px;font-size:11px;border:.5px solid var(--color-border-secondary);border-radius:20px;cursor:pointer;background:var(--color-background-primary);color:var(--color-text-secondary);}
.filter-btn.active{background:#0F1F5C;color:#fff;border-color:#0F1F5C;}
#map-tooltip{position:fixed;background:var(--color-background-primary);border:.5px solid var(--color-border-secondary);border-radius:var(--border-radius-md);padding:8px 10px;font-size:11px;pointer-events:none;opacity:0;transition:opacity .15s;z-index:999;max-width:220px;}
.risk-badge{font-size:10px;padding:2px 8px;border-radius:3px;font-weight:500;}
.cross-row{display:flex;flex-direction:column;gap:8px;}
.cross-item{border-radius:var(--border-radius-md);padding:10px 12px;border-left:3px solid;}
.map-legend{display:flex;flex-wrap:wrap;gap:8px;margin-top:8px;}
.leg-item{display:flex;align-items:center;gap:4px;font-size:11px;color:var(--color-text-secondary);}
.leg-sq{width:12px;height:12px;border-radius:2px;}
</style>

<div id="map-tooltip"></div>
<h2 class="sr-only">SBESOH v3 — Détail maladies SIMR, Top 5, analyse croisée One Health SE 22</h2>

<div class="app">
  <div class="topbar">
    <div style="display:flex;align-items:center;gap:9px;">
      <span class="badge-oh">ONE HEALTH</span>
      <div><div class="tb-brand">SBESOH — SIMR Surveillance · Analyse épidémiologique SE 22</div><div class="tb-sub">DVSSER · DSV/MAEP · FHI360 STRIDES · 26 mai 2026</div></div>
    </div>
    <div class="tb-right"><span><span class="sdot"></span>Pipeline actif</span><span><i class="ti ti-calendar" aria-hidden="true"></i> SE 22</span></div>
  </div>

  <div class="nav">
    <div class="ntab active" onclick="showTabV3('maladies',this)"><i class="ti ti-virus" aria-hidden="true"></i>Maladies SIMR</div>
    <div class="ntab" onclick="showTabV3('alertes',this)"><i class="ti ti-bell" aria-hidden="true"></i>Alertes <span style="background:#B71C1C;color:#fff;font-size:9px;padding:1px 5px;border-radius:3px;margin-left:3px;">3</span></div>
  </div>

  <div class="content">

    <!-- MALADIES SIMR -->
    <div id="tab-maladies" class="tab-content active">

      <!-- KPI ROW ÉTENDU -->
      <div class="krow" style="grid-template-columns:repeat(auto-fit,minmax(100px,1fr));">
        <div class="kpi"><div class="kl">Total cas SIMR SE22</div><div class="kv">1 247</div><div class="ks up"><i class="ti ti-trending-up"></i> +8% vs SE21</div></div>
        <div class="kpi"><div class="kl">Maladies actives</div><div class="kv">14</div><div class="ks">/ 22 maladies SIMR</div></div>
        <div class="kpi"><div class="kl">Signaux ROUGE</div><div class="kv" style="color:#B71C1C;">3</div><div class="ks up">Rage · MPox · H5N1</div></div>
        <div class="kpi"><div class="kl">Signaux ORANGE</div><div class="kv" style="color:#E65100;">4</div><div class="ks">Palu · Choléra · Anthrax · FMD</div></div>
        <div class="kpi"><div class="kl">Décès notifiés</div><div class="kv">14</div><div class="ks">CFR global 1.1%</div></div>
        <div class="kpi"><div class="kl">MPox confirmés</div><div class="kv" style="color:#B71C1C;">7</div><div class="ks up">+75% vs SE21 · 5 régions</div></div>
        <div class="kpi"><div class="kl">Zoonoses actives</div><div class="kv" style="color:#4A148C;">5</div><div class="ks">Rage · MPox · Lepto · Bruc. · H5</div></div>
        <div class="kpi"><div class="kl">Complétude SIMR</div><div class="kv" style="color:#F57F17;">76%</div><div class="ks">6 districts non déclarants</div></div>
      </div>

      <!-- SOUS-NAVIGATION SIMR INTERNE -->
      <div style="display:flex;gap:0;border-bottom:.5px solid var(--color-border-tertiary);margin-bottom:12px;overflow-x:auto;" id="simr-subnav">
        <div class="simr-stab active" onclick="showSIMRTab('vue-ensemble',this)" style="padding:7px 14px;font-size:11px;cursor:pointer;border-bottom:2px solid #0F1F5C;color:var(--color-text-primary);font-weight:500;white-space:nowrap;display:flex;align-items:center;gap:5px;"><i class="ti ti-table" aria-hidden="true"></i>Vue d'ensemble</div>
        <div class="simr-stab" onclick="showSIMRTab('tendances',this)" style="padding:7px 14px;font-size:11px;cursor:pointer;border-bottom:2px solid transparent;color:var(--color-text-secondary);white-space:nowrap;display:flex;align-items:center;gap:5px;"><i class="ti ti-chart-line" aria-hidden="true"></i>Tendances SE18–22</div>
        <div class="simr-stab" onclick="showSIMRTab('performance',this)" style="padding:7px 14px;font-size:11px;cursor:pointer;border-bottom:2px solid transparent;color:var(--color-text-secondary);white-space:nowrap;display:flex;align-items:center;gap:5px;"><i class="ti ti-activity" aria-hidden="true"></i>Performance SIMR</div>
        <div class="simr-stab" onclick="showSIMRTab('zoonoses-ihr',this)" style="padding:7px 14px;font-size:11px;cursor:pointer;border-bottom:2px solid transparent;color:var(--color-text-secondary);white-space:nowrap;display:flex;align-items:center;gap:5px;"><i class="ti ti-dna" aria-hidden="true"></i>Zoonoses & IHR</div>
        <div class="simr-stab" onclick="showSIMRTab('par-region',this)" style="padding:7px 14px;font-size:11px;cursor:pointer;border-bottom:2px solid transparent;color:var(--color-text-secondary);white-space:nowrap;display:flex;align-items:center;gap:5px;"><i class="ti ti-map-pin" aria-hidden="true"></i>Par région</div>
      </div>

      <!-- ── SOUS-ONGLET : VUE D'ENSEMBLE ── -->
      <div id="simr-tab-vue-ensemble" class="simr-stab-content">
        <div class="card">
          <div class="ct">
            <div class="ct-l"><i class="ti ti-table" style="color:#0F1F5C"></i>Tableau SIMR complet — SE 22</div>
            <div style="display:flex;gap:6px;">
              <button class="filter-btn active" id="fs-all" onclick="filterDisease('all')">Toutes</button>
              <button class="filter-btn" id="fs-alerte" onclick="filterDisease('alerte')">Alertes</button>
              <button class="filter-btn" id="fs-zoonose" onclick="filterDisease('zoonose')">Zoonoses</button>
            </div>
          </div>
          <div style="overflow-x:auto;">
            <table style="width:100%;border-collapse:collapse;font-size:11px;" id="disease-table">
              <thead><tr style="border-bottom:.5px solid var(--color-border-tertiary);background:var(--color-background-secondary);">
                <th style="text-align:left;padding:5px 8px;font-weight:500;color:var(--color-text-secondary);">Maladie</th>
                <th style="text-align:center;padding:5px 8px;font-weight:500;color:var(--color-text-secondary);">Cas SE22</th>
                <th style="text-align:center;padding:5px 8px;font-weight:500;color:var(--color-text-secondary);">Tendance</th>
                <th style="text-align:center;padding:5px 8px;font-weight:500;color:var(--color-text-secondary);">Décès</th>
                <th style="text-align:center;padding:5px 8px;font-weight:500;color:var(--color-text-secondary);">CFR</th>
                <th style="text-align:left;padding:5px 8px;font-weight:500;color:var(--color-text-secondary);">Régions touchées</th>
                <th style="text-align:center;padding:5px 8px;font-weight:500;color:var(--color-text-secondary);">Zoonose</th>
                <th style="text-align:center;padding:5px 8px;font-weight:500;color:var(--color-text-secondary);">Alerte</th>
              </tr></thead>
              <tbody id="disease-tbody"></tbody>
            </table>
          </div>
        </div>
        <div class="two">
          <div class="card">
            <div class="ct"><div class="ct-l"><i class="ti ti-chart-bar" style="color:#0F1F5C"></i>Cas par maladie — SE 22</div></div>
            <div style="position:relative;height:200px;"><canvas id="disease-bar"></canvas></div>
          </div>
          <div class="card">
            <div class="ct"><div class="ct-l"><i class="ti ti-chart-line" style="color:#E65100"></i>MPox — tendance SE 15–22</div></div>
            <div style="position:relative;height:200px;"><canvas id="mpox-chart"></canvas></div>
          </div>
        </div>
      </div>

      <!-- ── SOUS-ONGLET : TENDANCES SE18–22 ── -->
      <div id="simr-tab-tendances" class="simr-stab-content" style="display:none;">
        <div class="three">
          <div class="card">
            <div class="ct"><div class="ct-l"><i class="ti ti-chart-line" style="color:#B71C1C"></i>Zoonoses prioritaires</div></div>
            <div style="position:relative;height:180px;"><canvas id="trend-zoonoses"></canvas></div>
            <div style="font-size:10px;color:var(--color-text-secondary);margin-top:5px;">Rage · MPox · Leptospirose — SE18→SE22</div>
          </div>
          <div class="card">
            <div class="ct"><div class="ct-l"><i class="ti ti-chart-line" style="color:#1565C0"></i>Maladies vectorielles</div></div>
            <div style="position:relative;height:180px;"><canvas id="trend-vectorielles"></canvas></div>
            <div style="font-size:10px;color:var(--color-text-secondary);margin-top:5px;">Paludisme · Dengue — SE18→SE22</div>
          </div>
          <div class="card">
            <div class="ct"><div class="ct-l"><i class="ti ti-chart-line" style="color:#558B2F"></i>Maladies entériques</div></div>
            <div style="position:relative;height:180px;"><canvas id="trend-enteriques"></canvas></div>
            <div style="font-size:10px;color:var(--color-text-secondary);margin-top:5px;">Diarrhée · Choléra · GEA — SE18→SE22</div>
          </div>
        </div>
        <div class="card">
          <div class="ct"><div class="ct-l"><i class="ti ti-chart-area" style="color:#0F1F5C"></i>Tous signaux SIMR — Évolution SE18–22 (volume global)</div>
            <button class="btn-s" onclick="sendPrompt('Analyse les tendances épidémiologiques SE18-SE22 pour Madagascar : quelles maladies montrent une progression préoccupante ?')">Analyse tendance ↗</button>
          </div>
          <div style="position:relative;height:200px;"><canvas id="trend-global"></canvas></div>
        </div>
      </div>

      <!-- ── SOUS-ONGLET : PERFORMANCE SIMR ── -->
      <div id="simr-tab-performance" class="simr-stab-content" style="display:none;">
        <div class="three">
          <div class="card">
            <div class="ct"><div class="ct-l"><i class="ti ti-clock" style="color:#0F1F5C"></i>Délais 7-1-7 par signal</div></div>
            <div style="display:flex;flex-direction:column;gap:6px;" id="perf-717">
              <!-- rempli par JS -->
            </div>
          </div>
          <div class="card">
            <div class="ct"><div class="ct-l"><i class="ti ti-chart-bar-off" style="color:#B71C1C"></i>CFR par maladie — classement</div></div>
            <div style="position:relative;height:220px;"><canvas id="cfr-chart"></canvas></div>
          </div>
          <div class="card">
            <div class="ct"><div class="ct-l"><i class="ti ti-clipboard-check" style="color:#006064"></i>Complétude par région</div></div>
            <div style="display:flex;flex-direction:column;gap:5px;" id="perf-completude">
              <!-- rempli par JS -->
            </div>
          </div>
        </div>
        <div class="two">
          <div class="card">
            <div class="ct"><div class="ct-l"><i class="ti ti-chart-donut" style="color:#4A148C"></i>Répartition cas par catégorie</div></div>
            <div style="position:relative;height:200px;"><canvas id="cat-pie"></canvas></div>
          </div>
          <div class="card">
            <div class="ct"><div class="ct-l"><i class="ti ti-building-hospital" style="color:#E65100"></i>Districts en riposte active — SE22</div></div>
            <div style="display:flex;flex-direction:column;gap:7px;margin-top:4px;" id="riposte-list">
              <!-- rempli par JS -->
            </div>
          </div>
        </div>
      </div>

      <!-- ── SOUS-ONGLET : ZOONOSES & IHR ── -->
      <div id="simr-tab-zoonoses-ihr" class="simr-stab-content" style="display:none;">
        <!-- Bannière IHR -->
        <div style="background:linear-gradient(135deg,#4A148C,#7B1FA2);color:#fff;border-radius:8px;padding:12px 16px;margin-bottom:12px;">
          <div style="font-size:12px;font-weight:600;margin-bottom:4px;"><i class="ti ti-world" style="margin-right:5px"></i>Règlement Sanitaire International (RSI/IHR 2005) — Statut SE 22</div>
          <div style="font-size:11px;opacity:.85;line-height:1.6;">
            Notifications IHR en cours : <strong>Rage humaine (Art. 12)</strong> · <strong>MPox (surveillance IHR)</strong> · H5N1 OIE.
            Décision notification formelle OMS attendue sous 24h pour rage (critère Art. 12 rempli : événement grave, inattendu, risque propagation).
          </div>
        </div>
        <div class="two">
          <!-- Tableau zoonoses -->
          <div class="card">
            <div class="ct"><div class="ct-l"><i class="ti ti-dna" style="color:#B71C1C"></i>Agents pathogènes zoonoses SIMR — SE 22</div></div>
            <div style="overflow-x:auto;">
              <table style="width:100%;border-collapse:collapse;font-size:11px;">
                <thead><tr style="border-bottom:.5px solid var(--color-border-tertiary);background:var(--color-background-secondary);">
                  <th style="text-align:left;padding:5px 8px;font-weight:500;color:var(--color-text-secondary);">Agent</th>
                  <th style="text-align:left;padding:5px 8px;font-weight:500;color:var(--color-text-secondary);">Cas humains</th>
                  <th style="text-align:center;padding:5px 8px;font-weight:500;color:var(--color-text-secondary);">STREBIAN</th>
                  <th style="text-align:center;padding:5px 8px;font-weight:500;color:var(--color-text-secondary);">IHR</th>
                </tr></thead>
                <tbody id="zoonoses-ihr-tbody"></tbody>
              </table>
            </div>
          </div>
          <!-- Arbres décision IHR -->
          <div class="card">
            <div class="ct"><div class="ct-l"><i class="ti ti-sitemap" style="color:#4A148C"></i>Critères notification IHR — Décision SE 22</div></div>
            <div style="display:flex;flex-direction:column;gap:8px;" id="ihr-decision-list">
              <!-- rempli par JS -->
            </div>
          </div>
        </div>
        <div class="card">
          <div class="ct">
            <div class="ct-l"><i class="ti ti-shield-check" style="color:#006064"></i>Chaîne de transmission — Zoonoses confirmées SE 22</div>
            <button class="btn-s" onclick="sendPrompt('Analyse la chaîne de transmission des zoonoses SE22 Madagascar : rage Anjozorobe, leptospirose Boeny, MPox réservoir animal — recommandations One Health')">Analyse IA ↗</button>
          </div>
          <div style="display:grid;grid-template-columns:1fr 1fr;gap:10px;" id="transmission-chains">
            <!-- rempli par JS -->
          </div>
        </div>
      </div>

      <!-- ── SOUS-ONGLET : PAR RÉGION ── -->
      <div id="simr-tab-par-region" class="simr-stab-content" style="display:none;">
        <div class="card">
          <div class="ct"><div class="ct-l"><i class="ti ti-map-pin" style="color:#0F1F5C"></i>Charge épidémique SIMR par région — SE 22</div></div>
          <div style="position:relative;height:260px;"><canvas id="region-chart"></canvas></div>
        </div>
        <div class="two">
          <div class="card">
            <div class="ct"><div class="ct-l"><i class="ti ti-podium" style="color:#C9A84C"></i>Top 5 régions — charge totale SE22</div></div>
            <div style="display:flex;flex-direction:column;gap:6px;" id="region-top5-list"><!-- JS --></div>
          </div>
          <div class="card">
            <div class="ct"><div class="ct-l"><i class="ti ti-alert-triangle" style="color:#B71C1C"></i>Régions avec signaux multiples</div></div>
            <div style="display:flex;flex-direction:column;gap:6px;" id="region-multi-list"><!-- JS --></div>
          </div>
        </div>
      </div>

    </div>
    <!-- ALERTES -->
    <div id="tab-alertes" class="tab-content">
      <div class="card">
        <div class="ct"><div class="ct-l"><i class="ti ti-bell-ringing" style="color:#B71C1C" aria-hidden="true"></i>Alertes actives — SE 22</div></div>
        <div style="border-radius:var(--border-radius-md);padding:9px 11px;background:#FFEBEE;border:.5px solid #EF9F9F;margin-bottom:7px;">
          <div style="display:flex;align-items:center;gap:5px;margin-bottom:4px;"><span style="background:#B71C1C;color:#fff;font-size:9px;font-weight:500;padding:1px 6px;border-radius:3px;">B2 — ROUGE — ZOONOSE</span><span style="background:#FFCDD2;color:#B71C1C;font-size:9px;padding:1px 6px;border-radius:3px;">RAGE CONFIRMÉE</span></div>
          <div style="font-size:12px;">Signal croisé humain + animal — Anjozorobe (Analamanga). 1 cas humain mordu confirmé + STR-0442 rage bovine POSITIF. Investigation GIV + EMAR mobilisée. Prophylaxie post-exposition initiée.</div>
          <div style="font-size:10px;color:var(--color-text-secondary);margin-top:3px;"><i class="ti ti-clock" aria-hidden="true"></i> 3h · 7-1-7 : J3/7 · IHR notification en cours</div>
        </div>
        <div style="border-radius:var(--border-radius-md);padding:9px 11px;background:#FFF3E0;border:.5px solid #FBBF85;margin-bottom:7px;">
          <div style="display:flex;align-items:center;gap:5px;margin-bottom:4px;"><span style="background:#E65100;color:#fff;font-size:9px;font-weight:500;padding:1px 6px;border-radius:3px;">A1 — ORANGE — PALUDISME</span></div>
          <div style="font-size:12px;">Seuil épidémique paludisme Boeny. 312 cas SE22 vs moy. 198 (+57%). Pic hors saison — à surveiller MPox dans même région (2 cas confirmés).</div>
          <div style="font-size:10px;color:var(--color-text-secondary);margin-top:3px;"><i class="ti ti-clock" aria-hidden="true"></i> 7h · 7-1-7 : J1/7</div>
        </div>
        <div style="border-radius:var(--border-radius-md);padding:9px 11px;background:#FFFDE7;border:.5px solid #F9E06E;">
          <div style="display:flex;align-items:center;gap:5px;margin-bottom:4px;"><span style="background:#F57F17;color:#fff;font-size:9px;font-weight:500;padding:1px 6px;border-radius:3px;">MPox — SURVEILLANCE RENFORCÉE</span></div>
          <div style="font-size:12px;">7 cas confirmés SE22 (+75% vs SE21). Présence dans 5 régions. Tendance à la hausse depuis SE18. Aucun décès. Génotypage en cours au CNRE.</div>
          <div style="font-size:10px;color:var(--color-text-secondary);margin-top:3px;"><i class="ti ti-clock" aria-hidden="true"></i> Suivi hebdo · Notification Africa CDC</div>
        </div>
      </div>
      <div class="card">
        <div class="ct"><div class="ct-l"><i class="ti ti-list-check" aria-hidden="true" style="color:#0F1F5C"></i>Recommandations actionnables SE 22</div>
          <button class="btn-p" onclick="sendPrompt('Génère le résumé exécutif complet du Bulletin One Health SE22 : 1247 cas SIMR, paludisme Boeny +57%, MPox 7 cas 5 régions en hausse, rage zoonose Anjozorobe confirmée STREBIAN, leptospirose saison pluies, complétude 76%')"><i class="ti ti-sparkles" aria-hidden="true"></i>Résumé bulletin ↗</button>
        </div>
        <div id="reco-list"></div>
      </div>
    </div>

  </div>
</div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/d3/7.8.5/d3.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/topojson/3.0.2/topojson.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.js"></script>
<script>
function showTabV3(id, el) {
  document.querySelectorAll('.tab-content').forEach(t => t.classList.remove('active'));
  document.querySelectorAll('.ntab').forEach(t => t.classList.remove('active'));
  document.getElementById('tab-' + id).classList.add('active');
  el.classList.add('active');
  if (id === 'carte' && !mapDrawnV3) drawMap();
}

// ── DONNÉES MALADIES ────────────────────────────────────────────────────────
const diseases = [
  { name:'Paludisme', cas:312, prev:198, deces:2, cfr:'0.6%', regions:'Boeny, Atsinanana, Sofia, Melaky', zoonose:false, alerte:'orange', cat:'vectorielle', icon:'ti-bug' },
  { name:'IRA (pneumonie)', cas:287, prev:260, deces:3, cfr:'1.0%', regions:'Analamanga, Vakinankaratra, Haute Matsiatra', zoonose:false, alerte:'vert', cat:'respiratoire', icon:'ti-lungs' },
  { name:'Diarrhée aiguë', cas:198, prev:210, deces:1, cfr:'0.5%', regions:'Boeny, Atsinanana, Vakinankaratra', zoonose:false, alerte:'vert', cat:'gastro', icon:'ti-droplet' },
  { name:'Tuberculose', cas:87, prev:91, deces:4, cfr:'4.6%', regions:'Analamanga, Atsinanana, Diana', zoonose:false, alerte:'vert', cat:'respiratoire', icon:'ti-lungs' },
  { name:'Leptospirose', cas:54, prev:31, deces:2, cfr:'3.7%', regions:'Atsinanana, Analanjirofo, Sava', zoonose:true, alerte:'orange', cat:'zoonose', icon:'ti-droplet-half-2' },
  { name:'Paludisme grave', cas:48, prev:39, deces:2, cfr:'4.2%', regions:'Boeny, Melaky, Menabe', zoonose:false, alerte:'orange', cat:'vectorielle', icon:'ti-bug' },
  { name:'Méningite bact.', cas:23, prev:19, deces:1, cfr:'4.3%', regions:'Analamanga, Sofia', zoonose:false, alerte:'jaune', cat:'neurologique', icon:'ti-brain' },
  { name:'MPox', cas:7, prev:4, deces:0, cfr:'0%', regions:'Analamanga, Boeny, Diana, Atsinanana, SAVA', zoonose:true, alerte:'rouge', cat:'zoonose', icon:'ti-virus' },
  { name:'Rage humaine', cas:1, prev:0, deces:0, cfr:'—', regions:'Analamanga (Anjozorobe)', zoonose:true, alerte:'rouge', cat:'zoonose', icon:'ti-alert-triangle' },
  { name:'Choléra (suspect)', cas:11, prev:0, deces:0, cfr:'0%', regions:'Atsinanana (alerte)', zoonose:false, alerte:'orange', cat:'gastro', icon:'ti-droplet' },
  { name:'GEA', cas:89, prev:95, deces:0, cfr:'0%', regions:'Analamanga, Boeny, Sofia', zoonose:false, alerte:'vert', cat:'gastro', icon:'ti-droplet' },
  { name:'Dengue (suspect)', cas:14, prev:8, deces:0, cfr:'0%', regions:'Diana, SAVA', zoonose:false, alerte:'jaune', cat:'vectorielle', icon:'ti-bug' },
  { name:'Brucellose', cas:4, prev:2, deces:0, cfr:'0%', regions:'Vakinankaratra', zoonose:true, alerte:'jaune', cat:'zoonose', icon:'ti-virus' },
  { name:'Typhoïde', cas:29, prev:34, deces:0, cfr:'0%', regions:'Analamanga, Atsinanana', zoonose:false, alerte:'vert', cat:'gastro', icon:'ti-droplet' },
];

// ── TABLE MALADIES ──────────────────────────────────────────────────────────
const alerteColors = { rouge:'#B71C1C', orange:'#E65100', jaune:'#F57F17', vert:'#1B5E20' };
const alerteBg = { rouge:'#FFCDD2', orange:'#FFE0B2', jaune:'#FFF9C4', vert:'#E8F5E9' };

function renderDiseaseTable(filter) {
  const tbody = document.getElementById('disease-tbody');
  tbody.innerHTML = '';
  let filtered = diseases;
  if (filter === 'alerte') filtered = diseases.filter(d => d.alerte === 'rouge' || d.alerte === 'orange');
  if (filter === 'zoonose') filtered = diseases.filter(d => d.zoonose);
  filtered.forEach((d, i) => {
    const trend = d.cas > d.prev ? `<span style="color:#E65100;font-weight:500;">↑ +${d.cas - d.prev}</span>` : d.cas < d.prev ? `<span style="color:#1B5E20;font-weight:500;">↓ ${d.cas - d.prev}</span>` : `<span style="color:var(--color-text-secondary);">→ =</span>`;
    const tr = document.createElement('tr');
    tr.style = `border-bottom:.5px solid var(--color-border-tertiary);${i%2===0?'background:var(--color-background-secondary);':''}`;
    tr.innerHTML = `<td style="padding:5px 8px;font-weight:500;"><i class="ti ${d.icon}" style="color:${alerteColors[d.alerte]};font-size:13px;margin-right:5px;" aria-hidden="true"></i>${d.name}</td>
      <td style="text-align:center;padding:5px 8px;font-weight:500;font-size:13px;">${d.cas}</td>
      <td style="text-align:center;padding:5px 8px;">${trend}</td>
      <td style="text-align:center;padding:5px 8px;">${d.deces}</td>
      <td style="text-align:center;padding:5px 8px;font-weight:500;color:${parseFloat(d.cfr)>3?'#B71C1C':parseFloat(d.cfr)>1?'#E65100':'var(--color-text-primary)'};">${d.cfr}</td>
      <td style="padding:5px 8px;font-size:10px;color:var(--color-text-secondary);">${d.regions}</td>
      <td style="text-align:center;padding:5px 8px;"><span style="background:${d.zoonose?'#FFCDD2':'var(--color-background-secondary)'};color:${d.zoonose?'#B71C1C':'var(--color-text-secondary)'};font-size:9px;padding:1px 6px;border-radius:3px;">${d.zoonose?'OUI':'—'}</span></td>
      <td style="text-align:center;padding:5px 8px;"><span style="background:${alerteBg[d.alerte]};color:${alerteColors[d.alerte]};font-size:9px;padding:2px 7px;border-radius:3px;font-weight:500;">${d.alerte.toUpperCase()}</span></td>`;
    tbody.appendChild(tr);
  });
}
renderDiseaseTable('all');

function filterDisease(f) {
  document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
  document.getElementById('fs-' + f).classList.add('active');
  renderDiseaseTable(f);
}

// ── TOP 5 ───────────────────────────────────────────────────────────────────
const top5 = [
  {
    rank:1, name:'Paludisme', icon:'ti-bug', color:'#E65100', bg:'#FFF3E0', border:'#FBBF85',
    why:'Franchissement seuil épidémique Boeny (+57%). Pic hors saison. 2 cas graves. 360 cas cumulés si tendance maintenue SE23.',
    who:'Boeny, Melaky, Menabe — zones de transmission active',
    action:'Renforcement ACT + moustiquaires imprégné, investigation entomologique Boeny, alerte DRSP.',
    lien_animal:'Corrélation pluviométrie + diarrhée bovine Boeny (contamination eau ?)',
    risque:'ÉLEVÉ', semaine_pic:'SE 22–24', badge:'SEUIL ÉPIDÉMIQUE',
  },
  {
    rank:2, name:'MPox', icon:'ti-virus', color:'#B71C1C', bg:'#FFEBEE', border:'#EF9F9F',
    why:'7 cas SE22, +75% vs SE21, progression sur 5 semaines consécutives. 5 régions. Génotypage en cours. Aucun décès mais tendance préoccupante.',
    who:'Analamanga (3), Boeny (2), Diana (1), Atsinanana (1) — clusters urbains',
    action:'Renforcer recherche active contacts, isolement cas, envoyer échantillons au CNRE pour clade, notification Africa CDC.',
    lien_animal:'MPox : réservoir animal (rongeurs, primates) — surveiller MADSUR faune sauvage et marchés animaux',
    risque:'ÉLEVÉ', semaine_pic:'SE 23–26 si non contrôlé', badge:'PROGRESSION',
  },
  {
    rank:3, name:'Rage (zoonose)', icon:'ti-alert-triangle', color:'#B71C1C', bg:'#FFEBEE', border:'#EF9F9F',
    why:'1 cas humain mordu à Anjozorobe + résultat STREBIAN STR-0442 POSITIF rage bovine même district. Signal croisé One Health B2 ROUGE activé.',
    who:'Anjozorobe — District Analamanga. Population rurale exposée bovins + chiens errants.',
    action:'Prophylaxie post-exposition immédiate, campagne vaccination chiens Anjozorobe, investigation GIV + EMAR, notification IHR.',
    lien_animal:'LIEN DIRECT confirmé — rage bovine STREBIAN positive + cas humain même fokontany',
    risque:'CRITIQUE', semaine_pic:'Immédiat', badge:'ZOONOSE CONFIRMÉE',
  },
  {
    rank:4, name:'Leptospirose', icon:'ti-droplet-half-2', color:'#0F1F5C', bg:'#E6F1FB', border:'#85B7EB',
    why:'54 cas SE22 (+74% vs SE21 = 31). Saisonnalité : saison des pluies tardives côte Est. CFR 3.7% (2 décès). Sous-diagnostic probable.',
    who:'Atsinanana, Analanjirofo, SAVA — zones rizicoles côte Est',
    action:'Sensibiliser riziculteurs équipements de protection, tester suspicion fébrile en zone inondable, surveillance MADSUR rats.',
    lien_animal:'Réservoir rongeurs (MADSUR non couvert) — interface riziculture + eau stagnante + bovins',
    risque:'MODÉRÉ-ÉLEVÉ', semaine_pic:'SE 22–26 (pic saison pluies)', badge:'HAUSSE SAISONNIÈRE',
  },
  {
    rank:5, name:'Choléra (suspect)', icon:'ti-droplet', color:'#4A148C', bg:'#F3E5F5', border:'#CE93D8',
    why:'11 cas suspects Atsinanana (0 la semaine précédente). Notification immédiate — maladie à surveillance prioritaire. Confirmation labo en attente.',
    who:'Atsinanana — 1 district, foyer unique identifié, périmètre d\'investigation tracé',
    action:'Prélèvements coproculture urgents, chloration eau, isolement cas, investigation source commune, EMAR mobilisée.',
    lien_animal:'Pas de lien animal direct — surveillance contamination eau (rivières + point eau communautaire)',
    risque:'À SURVEILLER', semaine_pic:'SE 22 — évolution SE23 critique', badge:'NOTIFICATION IMMÉDIATE',
  },
];

const t5el = document.getElementById('top5-cards');
top5.forEach(d => {
  const riskBgColor = d.risque==='CRITIQUE'?'#FFCDD2':d.risque==='ÉLEVÉ'?'#FFE0B2':d.risque==='MODÉRÉ-ÉLEVÉ'?'#FFF9C4':'#E8F5E9';
  const riskTxtColor = d.risque==='CRITIQUE'||d.risque==='ÉLEVÉ'?'#B71C1C':d.risque==='MODÉRÉ-ÉLEVÉ'?'#E65100':'#1B5E20';
  t5el.innerHTML += `<div style="border:.5px solid ${d.border};background:${d.bg};border-radius:var(--border-radius-lg);padding:12px 14px;">
    <div style="display:flex;align-items:flex-start;gap:10px;margin-bottom:8px;">
      <div style="width:28px;height:28px;border-radius:50%;background:${d.color};display:flex;align-items:center;justify-content:center;flex-shrink:0;">
        <span style="font-size:14px;font-weight:500;color:#fff;">${d.rank}</span>
      </div>
      <div style="flex:1;">
        <div style="display:flex;align-items:center;gap:7px;flex-wrap:wrap;">
          <span style="font-size:14px;font-weight:500;color:${d.color};">${d.name}</span>
          <span style="background:${d.color};color:#fff;font-size:9px;padding:2px 7px;border-radius:3px;font-weight:500;">${d.badge}</span>
          <span style="background:${riskBgColor};color:${riskTxtColor};font-size:9px;padding:2px 7px;border-radius:3px;font-weight:500;">Risque ${d.risque}</span>
        </div>
        <div style="font-size:11px;color:var(--color-text-secondary);margin-top:2px;"><i class="ti ti-map-pin" style="font-size:11px;" aria-hidden="true"></i> ${d.who}</div>
      </div>
    </div>
    <div style="display:grid;grid-template-columns:1fr 1fr;gap:8px;font-size:11px;">
      <div>
        <div style="font-weight:500;color:var(--color-text-secondary);font-size:10px;margin-bottom:3px;">POURQUOI PRIORITAIRE</div>
        <div>${d.why}</div>
      </div>
      <div>
        <div style="font-weight:500;color:var(--color-text-secondary);font-size:10px;margin-bottom:3px;">ACTION REQUISE</div>
        <div>${d.action}</div>
      </div>
    </div>
    <div style="margin-top:8px;background:rgba(0,0,0,0.04);border-radius:var(--border-radius-md);padding:6px 9px;font-size:11px;">
      <span style="font-weight:500;color:${d.color};"><i class="ti ti-arrows-cross" style="font-size:11px;" aria-hidden="true"></i> Lien One Health :</span> ${d.lien_animal}
    </div>
  </div>`;
});

// ── ANALYSE CROISÉE ─────────────────────────────────────────────────────────
const crossSignals = [
  {
    id:'OH-01', title:'Rage bovine + cas humain — Anjozorobe (Analamanga)', level:'ROUGE', color:'#B71C1C', bg:'#FFEBEE',
    human:'1 cas mordu, fièvre + confusion — hospitalisé CSB Anjozorobe. Prophylaxie post-exposition initiée.',
    animal:'Mortalité bovine 8% en 48h — 3 bovins avec signes neurologiques. GIV prélèvement STR-0442.',
    strebian:'POSITIF — Sérologie rage bovine confirmée (résultat J+5).',
    env:'Zone d\'élevage extensif + chiens errants non vaccinés. Interface bovins-chiens-humains dense.',
    action:'Investigation One Health Anjozorobe : équipe mixte DVSSER + DSV + GIV. Vaccination chiens district. Notification IHR.',
    cadre717:'Détection J0 ✓ — Notification J3 (en cours) — Riposte J7 (objectif)',
  },
  {
    id:'OH-02', title:'Paludisme Boeny + diarrhée bovine — Possible contamination eau', level:'ORANGE', color:'#E65100', bg:'#FFF3E0',
    human:'312 cas paludisme Boeny (+57%). 89 cas GEA dont 18 pédiatriques. Cluster spatial : 3 fokontany riverains.',
    animal:'18 cas diarrhée bovine hémorragique Boeny — même fokontany que les cas humains GEA.',
    strebian:'STR-0444 culture Charbon : NÉGATIF. Pas d\'agent zoonose identifié pour diarrhée.',
    env:'Précipitations inhabituelles mai 2026 (anomalie +40%) — points d\'eau communautaires non chlorés signalés.',
    action:'Chloration points eau prioritaires, enquête entomologique malaria, prélèvements eau MEEF urgents, surveillance GEA.',
    cadre717:'Détection J0 ✓ — Notification J1 ✓ — Investigation eau en cours',
  },
  {
    id:'OH-03', title:'MPox — Surveillance interface humain-animal', level:'JAUNE', color:'#F57F17', bg:'#FFFDE7',
    human:'7 cas confirmés SE22 (+75%). Clusters: Analamanga (3), Boeny (2), Diana (1), Atsinanana (1). Clade en cours de détermination.',
    animal:'Aucun signal MADSUR faune sauvage actuellement — réservoir rongeurs/primates non surveillé.',
    strebian:'Pas de prélèvement animal MPox. À initier : surveillance marchés animaux Antananarivo et Mahajanga.',
    env:'Marchés de viande sauvage / chasse : 2 cas déclarent avoir été en contact avec gibier dans les 21 jours.',
    action:'Initier surveillance MPox dans MADSUR (rongeurs, marchés animaux). Enquête expositions des 7 cas. Génotypage CNRE.',
    cadre717:'Détection J0 ✓ — Notification Africa CDC SE22 — Enquête expositions en cours',
  },
  {
    id:'OH-04', title:'Leptospirose côte Est — Interface riziculture-rongeurs-eau', level:'ORANGE', color:'#0F1F5C', bg:'#E6F1FB',
    human:'54 cas SE22, +74% vs SE21. CFR 3.7% (2 décès). Atsinanana, Analanjirofo, SAVA — agriculteurs rizicoles 80%.',
    animal:'Rongeurs (Rattus rattus) : réservoir principal. Pas de données MADSUR rongeurs actuellement.',
    strebian:'Pas de prélèvement rongeurs — à initier en priorité Atsinanana.',
    env:'Saison des pluies tardives : inondations rizières. Lacs et rivières débordants = amplification transmission.',
    action:'Équipement EPI riziculteurs (bottes), dératisation zones agricoles, surveillance eau (MEEF), sensibilisation via AC.',
    cadre717:'Surveillance renforcée — Pas d\'alerte IHR mais tendance préoccupante',
  },
];

const crossEl = document.getElementById('cross-signals');
crossSignals.forEach(s => {
  const lvlBg = { ROUGE:'#FFCDD2', ORANGE:'#FFE0B2', JAUNE:'#FFF9C4' };
  crossEl.innerHTML += `<div style="border-left:3px solid ${s.color};background:${s.bg};border-radius:var(--border-radius-md);padding:11px 13px;border:.5px solid ${s.color}33;">
    <div style="display:flex;align-items:center;gap:7px;margin-bottom:8px;">
      <span style="font-size:11px;font-weight:500;color:var(--color-text-secondary);">${s.id}</span>
      <span style="flex:1;font-size:13px;font-weight:500;color:${s.color};">${s.title}</span>
      <span style="background:${lvlBg[s.level]||s.bg};color:${s.color};font-size:9px;padding:2px 8px;border-radius:3px;font-weight:500;">${s.level}</span>
    </div>
    <div style="display:grid;grid-template-columns:1fr 1fr 1fr;gap:8px;font-size:11px;margin-bottom:8px;">
      <div style="background:rgba(255,255,255,0.6);border-radius:6px;padding:7px 9px;">
        <div style="font-size:10px;font-weight:500;color:#0F1F5C;margin-bottom:3px;"><i class="ti ti-user" aria-hidden="true"></i> Signal humain</div>
        <div>${s.human}</div>
      </div>
      <div style="background:rgba(255,255,255,0.6);border-radius:6px;padding:7px 9px;">
        <div style="font-size:10px;font-weight:500;color:#006064;margin-bottom:3px;"><i class="ti ti-pig" aria-hidden="true"></i> Signal animal</div>
        <div>${s.animal}</div>
      </div>
      <div style="background:rgba(255,255,255,0.6);border-radius:6px;padding:7px 9px;">
        <div style="font-size:10px;font-weight:500;color:#546E7A;margin-bottom:3px;"><i class="ti ti-trees" aria-hidden="true"></i> Environnement</div>
        <div>${s.env}</div>
      </div>
    </div>
    <div style="display:grid;grid-template-columns:1fr 1fr;gap:8px;font-size:11px;">
      <div style="background:rgba(255,255,255,0.6);border-radius:6px;padding:7px 9px;">
        <div style="font-size:10px;font-weight:500;color:#C9A84C;margin-bottom:3px;"><i class="ti ti-flask" aria-hidden="true"></i> STREBIAN</div>
        <div>${s.strebian}</div>
      </div>
      <div style="background:rgba(255,255,255,0.6);border-radius:6px;padding:7px 9px;">
        <div style="font-size:10px;font-weight:500;color:#1B5E20;margin-bottom:3px;"><i class="ti ti-list-check" aria-hidden="true"></i> Action + Cadre 7-1-7</div>
        <div>${s.action}</div>
        <div style="margin-top:4px;font-size:10px;color:var(--color-text-secondary);">${s.cadre717}</div>
      </div>
    </div>
  </div>`;
});

// ── TABLE ZOONOSES ──────────────────────────────────────────────────────────
const zoonoses = [
  { agent:'Virus rage (RABV)', human:'1 cas mordu, fièvre, confusion', animal:'Bovins — mortalité 8%', zone:'Anjozorobe / Analamanga', strebian:'POSITIF (STR-0442)', prio:'CRITIQUE' },
  { agent:'Leptospira spp.', human:'54 cas, CFR 3.7%', animal:'Rongeurs (non testés)', zone:'Atsinanana, Analanjirofo, SAVA', strebian:'Non initié', prio:'HAUTE' },
  { agent:'Monkeypox virus (MPox)', human:'7 cas confirmés', animal:'Rongeurs/marchés ? (non testé)', zone:'5 régions', strebian:'Non initié', prio:'HAUTE' },
  { agent:'Brucella spp.', human:'4 cas suspects', animal:'Bovins Vakinankaratra (STR-0446 en cours)', zone:'Vakinankaratra', strebian:'En cours', prio:'MODÉRÉE' },
  { agent:'Influenza A (H5?)', human:'0 cas humains', animal:'Volailles Boeny — chute ponte', zone:'Boeny', strebian:'En cours (STR-0443)', prio:'MODÉRÉE' },
];
const ztbody = document.getElementById('zoonose-tbody');
const prioBg = { CRITIQUE:'#FFCDD2', HAUTE:'#FFE0B2', MODÉRÉE:'#FFF9C4' };
const prioTxt = { CRITIQUE:'#B71C1C', HAUTE:'#E65100', MODÉRÉE:'#F57F17' };
zoonoses.forEach((z, i) => {
  const tr = document.createElement('tr');
  tr.style = `border-bottom:.5px solid var(--color-border-tertiary);${i%2===0?'background:var(--color-background-secondary);':''}`;
  tr.innerHTML = `<td style="padding:5px 8px;font-weight:500;">${z.agent}</td>
    <td style="padding:5px 8px;">${z.human}</td>
    <td style="padding:5px 8px;">${z.animal}</td>
    <td style="padding:5px 8px;font-size:10px;color:var(--color-text-secondary);">${z.zone}</td>
    <td style="text-align:center;padding:5px 8px;"><span style="background:${z.strebian==='POSITIF (STR-0442)'?'#FFCDD2':z.strebian==='Non initié'?'var(--color-background-secondary)':'#FFF9C4'};color:${z.strebian==='POSITIF (STR-0442)'?'#B71C1C':z.strebian==='Non initié'?'var(--color-text-secondary)':'#F57F17'};font-size:9px;padding:1px 6px;border-radius:3px;">${z.strebian}</span></td>
    <td style="text-align:center;padding:5px 8px;"><span style="background:${prioBg[z.prio]||'#E8F5E9'};color:${prioTxt[z.prio]||'#1B5E20'};font-size:9px;padding:2px 7px;border-radius:3px;font-weight:500;">${z.prio}</span></td>`;
  ztbody.appendChild(tr);
});

// ── RECOMMANDATIONS ─────────────────────────────────────────────────────────
const recos = [
  { niveau:'National (DVSSER + DSV)', icon:'ti-building', color:'#0F1F5C', bg:'#E6F1FB', actions:[
    'Activer investigation One Health Anjozorobe — équipe mixte DVSSER + DSV + GIV dans les 24h (rage confirmée).',
    'Déclencher protocole notification IHR pour cas rage humaine + notification Africa CDC pour MPox (7 cas, progression).',
    'Initier prélèvements MADSUR rongeurs (Atsinanana) et marchés animaux (Antananarivo/Mahajanga) pour MPox et leptospirose.',
  ]},
  { niveau:'Régional — Boeny', icon:'ti-map-pin', color:'#E65100', bg:'#FFF3E0', actions:[
    'Renforcer distribution ACT dans les 10 SDSP Boeny — seuil paludisme franchi.',
    'Envoyer échantillons volailles au RESAMAD pour PCR influenza A (résultat STR-0443 attendu sous 5j).',
    'Investiguer point eau commun bovins-humains — 3 fokontany GEA + diarrhée bovine simultanées.',
  ]},
  { niveau:'Régional — Analamanga', icon:'ti-map-pin', color:'#B71C1C', bg:'#FFEBEE', actions:[
    'Lancer campagne vaccination chiens district Anjozorobe dans les 7 jours — prévention rage secondaire.',
    'Tracer et contacter tous les contacts du cas MPox Analamanga (3 cas — réseau de contacts à identifier).',
  ]},
  { niveau:'Districts non-déclarants (12 SDSP)', icon:'ti-school', color:'#F57F17', bg:'#FFFDE7', actions:[
    'Transmettre rapport SIMR SE22 avant vendredi 28/05 — alerte E1 active, complétude nationale 76%.',
    'Signaler immédiatement toute morsure animale + fièvre, tout cas suspect MPox (éruption vésiculaire), tout foyer diarrhée hémorragique bovin.',
  ]},
];
const recoEl = document.getElementById('reco-list');
recos.forEach(r => {
  recoEl.innerHTML += `<div style="border-radius:var(--border-radius-md);padding:9px 11px;background:${r.bg};border:.5px solid ${r.color}33;margin-bottom:6px;">
    <div style="display:flex;align-items:center;gap:6px;margin-bottom:6px;"><i class="ti ${r.icon}" style="color:${r.color};font-size:14px;" aria-hidden="true"></i><span style="font-size:12px;font-weight:500;color:${r.color};">${r.niveau}</span></div>
    ${r.actions.map(a=>`<div style="display:flex;align-items:flex-start;gap:6px;margin-bottom:4px;"><i class="ti ti-arrow-right" style="color:${r.color};font-size:12px;margin-top:2px;flex-shrink:0;" aria-hidden="true"></i><span style="font-size:11px;">${a}</span></div>`).join('')}
  </div>`;
});

// ── MPox par région ─────────────────────────────────────────────────────────
const mpoxRegions = [
  { r:'Analamanga', cas:3, trend:'+1', contact:'Marché Isotry — cluster identifié' },
  { r:'Boeny', cas:2, trend:'+2', contact:'Contact direct lésions actives confirmé' },
  { r:'Diana', cas:1, trend:'Nouveau', contact:'Retour voyage — cas index à identifier' },
  { r:'Atsinanana', cas:1, trend:'Nouveau', contact:'Professionnel de santé — EPI renforcé' },
];
const mpoxEl = document.getElementById('mpox-map-list');
mpoxRegions.forEach((m, i) => {
  mpoxEl.innerHTML += `<div style="display:flex;align-items:center;gap:8px;padding:6px 8px;background:${i%2===0?'var(--color-background-secondary)':'var(--color-background-primary)'};border-radius:var(--border-radius-md);font-size:11px;">
    <span style="font-weight:500;flex:1;">${m.r}</span>
    <span style="font-weight:500;color:#B71C1C;">${m.cas} cas</span>
    <span style="background:#FFCDD2;color:#B71C1C;font-size:9px;padding:1px 5px;border-radius:3px;">${m.trend}</span>
  </div>
  <div style="font-size:10px;color:var(--color-text-secondary);padding:2px 8px 5px;">${m.contact}</div>`;
});

// ── CARTE ────────────────────────────────────────────────────────────────────
const regionData = {
  'Analamanga':      { cas:298, completude:84, madsur:5, alerte:'rouge',  mpox:3, lepto:8,  palu:12, maladie_dom:'Rage+MPox' },
  'Boeny':           { cas:312, completude:78, madsur:4, alerte:'orange', mpox:2, lepto:0,  palu:312, maladie_dom:'Paludisme' },
  'Atsinanana':      { cas:187, completude:81, madsur:3, alerte:'jaune',  mpox:1, lepto:28, palu:0,  maladie_dom:'Leptospirose' },
  'Vakinankaratra':  { cas:142, completude:72, madsur:4, alerte:'jaune',  mpox:0, lepto:0,  palu:0,  maladie_dom:'Brucellose/IRA' },
  'Sofia':           { cas:89,  completude:65, madsur:3, alerte:'jaune',  mpox:0, lepto:0,  palu:42, maladie_dom:'Paludisme' },
  'Betsiboka':       { cas:43,  completude:70, madsur:2, alerte:'vert',   mpox:0, lepto:0,  palu:18, maladie_dom:'Paludisme' },
  'Alaotra-Mangoro': { cas:76,  completude:75, madsur:0, alerte:'vert',   mpox:0, lepto:0,  palu:5,  maladie_dom:'IRA' },
  'Haute Matsiatra': { cas:54,  completude:68, madsur:0, alerte:'vert',   mpox:0, lepto:0,  palu:0,  maladie_dom:'Tuberculose' },
  "Amoron'i Mania":  { cas:38,  completude:62, madsur:1, alerte:'jaune',  mpox:0, lepto:0,  palu:0,  maladie_dom:'GEA' },
  'Diana':           { cas:61,  completude:55, madsur:0, alerte:'jaune',  mpox:1, lepto:0,  palu:0,  maladie_dom:'MPox+Dengue' },
  'Sava':            { cas:47,  completude:58, madsur:1, alerte:'vert',   mpox:0, lepto:12, palu:0,  maladie_dom:'Leptospirose' },
  'Analanjirofo':    { cas:29,  completude:69, madsur:0, alerte:'vert',   mpox:0, lepto:14, palu:0,  maladie_dom:'Leptospirose' },
  'Bongolava':       { cas:22,  completude:71, madsur:0, alerte:'vert',   mpox:0, lepto:0,  palu:8,  maladie_dom:'Paludisme' },
  'Itasy':           { cas:31,  completude:76, madsur:0, alerte:'vert',   mpox:0, lepto:0,  palu:0,  maladie_dom:'IRA' },
  'Menabe':          { cas:19,  completude:60, madsur:0, alerte:'vert',   mpox:0, lepto:0,  palu:10, maladie_dom:'Paludisme' },
  'Melaky':          { cas:11,  completude:52, madsur:0, alerte:'jaune',  mpox:0, lepto:0,  palu:8,  maladie_dom:'Paludisme' },
  'Atsimo-Andrefana':{ cas:33,  completude:48, madsur:0, alerte:'jaune',  mpox:0, lepto:0,  palu:0,  maladie_dom:'Données manquantes' },
  'Anosy':           { cas:15,  completude:54, madsur:0, alerte:'vert',   mpox:0, lepto:0,  palu:0,  maladie_dom:'GEA' },
  'Androy':          { cas:8,   completude:43, madsur:0, alerte:'jaune',  mpox:0, lepto:0,  palu:0,  maladie_dom:'Données manquantes' },
  'Atsimo-Atsinanana':{ cas:24, completude:57, madsur:0, alerte:'vert',   mpox:0, lepto:0,  palu:0,  maladie_dom:'Diarrhée' },
  'Ihorombe':        { cas:12,  completude:45, madsur:0, alerte:'jaune',  mpox:0, lepto:0,  palu:0,  maladie_dom:'Données manquantes' },
  'Vatovavy':        { cas:17,  completude:41, madsur:0, alerte:'jaune',  mpox:0, lepto:0,  palu:0,  maladie_dom:'Données manquantes' },
};

const maladieColors = {
  'Rage+MPox':'#B71C1C', 'MPox+Dengue':'#B71C1C', 'Paludisme':'#1565C0',
  'Leptospirose':'#006064', 'Brucellose/IRA':'#4A148C', 'Tuberculose':'#546E7A',
  'IRA':'#546E7A', 'GEA':'#558B2F', 'Diarrhée':'#558B2F', 'Données manquantes':'#B0B0B0',
};

let currentFilter = 'humain', mapDrawnV3 = false;
function getColor(name, filter) {
  const d = regionData[name];
  if (!d) return '#E0E0E0';
  if (filter === 'humain') {
    const v = d.cas;
    if (v>250) return '#0C447C'; if (v>150) return '#185FA5'; if (v>80) return '#378ADD';
    if (v>40) return '#85B7EB'; if (v>10) return '#B5D4F4'; return '#E6F1FB';
  }
  if (filter === 'maladie') return maladieColors[d.maladie_dom] || '#B0B0B0';
  if (filter === 'animal') {
    const v = d.madsur;
    if (v>=4) return '#085041'; if (v>=2) return '#1D9E75'; if (v>=1) return '#5DCAA5'; return '#E1F5EE';
  }
  if (filter === 'alerte') {
    if (d.alerte==='rouge') return '#B71C1C'; if (d.alerte==='orange') return '#E65100';
    if (d.alerte==='jaune') return '#F57F17'; return '#1B5E20';
  }
}
function getLegend(f) {
  if (f==='humain') return [['#0C447C','>250'],['#378ADD','80–250'],['#85B7EB','40–80'],['#B5D4F4','10–40'],['#E6F1FB','<10']];
  if (f==='maladie') return [['#B71C1C','Rage/MPox'],['#1565C0','Paludisme'],['#006064','Leptospirose'],['#4A148C','Brucellose'],['#546E7A','IRA/TB'],['#B0B0B0','Données manq.']];
  if (f==='animal') return [['#085041','≥4 signaux'],['#1D9E75','2–3'],['#5DCAA5','1'],['#E1F5EE','Aucun']];
  if (f==='alerte') return [['#B71C1C','ROUGE'],['#E65100','ORANGE'],['#F57F17','JAUNE'],['#1B5E20','VERT']];
}
function setFilter(f) {
  currentFilter = f;
  document.querySelectorAll('#tab-carte .filter-btn').forEach(b=>b.classList.remove('active'));
  document.getElementById('f-'+f).classList.add('active');
  document.getElementById('map-mode-label').textContent={humain:'Cas humains SIMR',maladie:'Maladie dominante',animal:'MADSUR signaux',alerte:'Niveau alerte OH'}[f];
  if (svgSel) svgSel.selectAll('path').attr('fill',d=>getColor(d.properties.name,currentFilter));
  const leg=document.getElementById('map-legend');
  leg.innerHTML='';
  getLegend(f).forEach(([c,l])=>{ leg.innerHTML+=`<div class="leg-item"><div class="leg-sq" style="background:${c};"></div>${l}</div>`; });
}
let svgSel;
function drawMap() {
  mapDrawnV3=true;
  const container=document.getElementById('map-container');
  const W=container.offsetWidth||270, H=W*2.0;
  const svg=d3.select('#map-container').append('svg').attr('viewBox',`0 0 ${W} ${H}`).attr('width','100%').style('display','block');
  svgSel=svg;
  const tooltip=document.getElementById('map-tooltip');
  d3.json('https://cdn.jsdelivr.net/npm/datamaps@0.5.10/src/js/data/mdg.topo.json').then(topo=>{
    const features=topojson.feature(topo,topo.objects.mdg).features;
    const proj=d3.geoMercator().fitSize([W,H],topojson.feature(topo,topo.objects.mdg));
    const path=d3.geoPath(proj);
    svg.selectAll('path').data(features).join('path')
      .attr('d',path).attr('stroke','#fff').attr('stroke-width',0.6)
      .attr('fill',d=>getColor(d.properties.name,currentFilter)).attr('cursor','pointer')
      .on('mousemove',function(event,d){
        const name=d.properties.name, rd=regionData[name];
        if(!rd) return;
        const ac={rouge:'#B71C1C',orange:'#E65100',jaune:'#F57F17',vert:'#1B5E20'};
        const al={rouge:'ROUGE',orange:'ORANGE',jaune:'JAUNE',vert:'VERT'};
        tooltip.innerHTML=`<div style="font-weight:500;margin-bottom:3px;">${name}</div>
          <div style="color:var(--color-text-secondary);">Cas SIMR: <strong>${rd.cas}</strong> · Maladie: <strong>${rd.maladie_dom}</strong></div>
          ${rd.mpox>0?`<div style="color:#B71C1C;">MPox: <strong>${rd.mpox} cas</strong></div>`:''}
          ${rd.palu>30?`<div style="color:#1565C0;">Paludisme: <strong>${rd.palu} cas</strong></div>`:''}
          ${rd.lepto>0?`<div style="color:#006064;">Leptospirose: <strong>${rd.lepto} cas</strong></div>`:''}
          <div style="margin-top:3px;"><span style="background:${ac[rd.alerte]};color:#fff;font-size:9px;padding:1px 6px;border-radius:3px;">${al[rd.alerte]}</span></div>`;
        tooltip.style.opacity='1'; tooltip.style.left=(event.clientX+12)+'px'; tooltip.style.top=(event.clientY-10)+'px';
      })
      .on('mouseleave',()=>{ tooltip.style.opacity='0'; })
      .on('click',function(event,d){
        const name=d.properties.name, rd=regionData[name];
        if(!rd) return;
        const ac={rouge:'#B71C1C',orange:'#E65100',jaune:'#F57F17',vert:'#1B5E20'};
        const ab={rouge:'#FFEBEE',orange:'#FFF3E0',jaune:'#FFFDE7',vert:'#E8F5E9'};
        const al={rouge:'ROUGE',orange:'ORANGE',jaune:'JAUNE',vert:'VERT'};
        document.getElementById('region-title').textContent=name;
        document.getElementById('region-detail').innerHTML=`
          <div style="display:flex;gap:5px;flex-wrap:wrap;margin-bottom:7px;">
            <span style="background:${ab[rd.alerte]};color:${ac[rd.alerte]};font-size:10px;padding:2px 8px;border-radius:3px;font-weight:500;">${al[rd.alerte]}</span>
            <span style="background:#E6F1FB;color:#0F1F5C;font-size:10px;padding:2px 8px;border-radius:3px;">${rd.maladie_dom}</span>
          </div>
          <div style="display:grid;grid-template-columns:1fr 1fr;gap:5px;font-size:11px;">
            <div style="background:var(--color-background-secondary);border-radius:6px;padding:6px 8px;"><div style="color:var(--color-text-secondary);font-size:10px;">Cas SIMR</div><div style="font-size:15px;font-weight:500;">${rd.cas}</div></div>
            <div style="background:var(--color-background-secondary);border-radius:6px;padding:6px 8px;"><div style="color:var(--color-text-secondary);font-size:10px;">MADSUR</div><div style="font-size:15px;font-weight:500;color:#006064;">${rd.madsur}</div></div>
            ${rd.mpox>0?`<div style="background:#FFEBEE;border-radius:6px;padding:6px 8px;"><div style="color:#B71C1C;font-size:10px;font-weight:500;">MPox</div><div style="font-size:15px;font-weight:500;color:#B71C1C;">${rd.mpox}</div></div>`:''}
            ${rd.palu>0?`<div style="background:#E3F2FD;border-radius:6px;padding:6px 8px;"><div style="color:#1565C0;font-size:10px;font-weight:500;">Paludisme</div><div style="font-size:15px;font-weight:500;color:#1565C0;">${rd.palu}</div></div>`:''}
            ${rd.lepto>0?`<div style="background:#E0F7FA;border-radius:6px;padding:6px 8px;"><div style="color:#006064;font-size:10px;font-weight:500;">Leptospirose</div><div style="font-size:15px;font-weight:500;color:#006064;">${rd.lepto}</div></div>`:''}
          </div>
          <div style="margin-top:7px;"><button class="btn-s" style="font-size:10px;" onclick="sendPrompt('Analyse One Health détaillée région ${name} SE22')">Analyse ${name} ↗</button></div>`;
        svg.selectAll('path').attr('stroke','#fff').attr('stroke-width',0.6);
        d3.select(this).attr('stroke','#C9A84C').attr('stroke-width',2);
      });
    setFilter('humain');
  });
}

// ── CHARTS ──────────────────────────────────────────────────────────────────
new Chart(document.getElementById('disease-bar'),{
  type:'bar',
  data:{ labels:['Palu.','IRA','Diarrhée','TB','GEA','Lepto.','Palu.grave','Méning.','Typhoïde','Dengue','Choléra','Brucellose','MPox','Rage'],
    datasets:[{ data:[312,287,198,87,89,54,48,23,29,14,11,4,7,1],
      backgroundColor:['#1565C0','#546E7A','#558B2F','#546E7A','#558B2F','#006064','#1565C0','#4A148C','#558B2F','#E65100','#4A148C','#F57F17','#B71C1C','#B71C1C'] }] },
  options:{ indexAxis:'y', responsive:true, maintainAspectRatio:false, plugins:{legend:{display:false}},
    scales:{ x:{ticks:{font:{size:9}}}, y:{ticks:{font:{size:9},autoSkip:false}} } }
});

new Chart(document.getElementById('mpox-chart'),{
  type:'line',
  data:{ labels:['SE15','SE16','SE17','SE18','SE19','SE20','SE21','SE22'],
    datasets:[{ label:'Cas MPox', data:[1,2,1,3,2,4,4,7], borderColor:'#B71C1C', backgroundColor:'rgba(183,28,28,0.1)', fill:true, tension:0.3, pointBackgroundColor:'#B71C1C', pointRadius:4 }] },
  options:{ responsive:true, maintainAspectRatio:false, plugins:{legend:{display:false}},
    scales:{ x:{ticks:{font:{size:10},autoSkip:false}}, y:{ticks:{font:{size:10}},beginAtZero:true} } }
});

new Chart(document.getElementById('convergence-chart'),{
  type:'bar',
  data:{ labels:['Analamanga','Boeny','Vaki.','Atsinanana','Sofia'],
    datasets:[
      { label:'Cas humains SIMR', data:[298,312,142,187,89], backgroundColor:'rgba(15,31,92,0.7)' },
      { label:'Signaux MADSUR ×20', data:[100,80,80,60,60], backgroundColor:'rgba(0,96,100,0.7)' },
    ] },
  options:{ responsive:true, maintainAspectRatio:false, plugins:{ legend:{display:false} },
    scales:{ x:{ticks:{font:{size:9},autoSkip:false}}, y:{ticks:{font:{size:9}}} } }
});

new Chart(document.getElementById('timeline-chart'),{
  type:'line',
  data:{ labels:['SE18','SE19','SE20','SE21','SE22'],
    datasets:[
      { label:'Cas SIMR /10', data:[98,105,134,115,125], borderColor:'#0F1F5C', backgroundColor:'rgba(15,31,92,0.07)', fill:true, tension:0.3, pointRadius:3 },
      { label:'Signaux MADSUR', data:[12,14,18,20,23], borderColor:'#006064', backgroundColor:'rgba(0,96,100,0.07)', fill:true, tension:0.3, pointRadius:3, borderDash:[4,2] },
    ] },
  options:{ responsive:true, maintainAspectRatio:false,
    plugins:{ legend:{ display:true, labels:{ font:{size:10}, boxWidth:12 } } },
    scales:{ x:{ticks:{font:{size:10},autoSkip:false}}, y:{ticks:{font:{size:10}}} } }
});

new Chart(document.getElementById('risk-matrix'),{
  type:'bubble',
  data:{ datasets:[
    { label:'Paludisme', data:[{x:3.8,y:4.2,r:14}], backgroundColor:'rgba(21,101,192,0.75)' },
    { label:'MPox', data:[{x:3.2,y:3.8,r:10}], backgroundColor:'rgba(183,28,28,0.75)' },
    { label:'Rage', data:[{x:1.5,y:4.9,r:8}], backgroundColor:'rgba(183,28,28,0.75)' },
    { label:'Leptospirose', data:[{x:3.5,y:3.5,r:9}], backgroundColor:'rgba(0,96,100,0.75)' },
    { label:'Choléra', data:[{x:2.2,y:4.5,r:7}], backgroundColor:'rgba(74,20,140,0.75)' },
    { label:'IRA', data:[{x:4.5,y:2.0,r:12}], backgroundColor:'rgba(84,110,122,0.6)' },
    { label:'TB', data:[{x:3.0,y:2.5,r:7}], backgroundColor:'rgba(84,110,122,0.6)' },
    { label:'Brucellose', data:[{x:1.8,y:3.2,r:5}], backgroundColor:'rgba(245,127,23,0.75)' },
    { label:'Influenza av.', data:[{x:2.5,y:4.0,r:6}], backgroundColor:'rgba(230,81,0,0.75)' },
  ] },
  options:{ responsive:true, maintainAspectRatio:false,
    plugins:{ legend:{ display:false }, tooltip:{ callbacks:{ label: ctx=>`${ctx.dataset.label}` } } },
    scales:{
      x:{ min:0, max:5.5, title:{ display:true, text:'Probabilité →', font:{size:10} }, ticks:{font:{size:9}} },
      y:{ min:0, max:5.5, title:{ display:true, text:'Impact →', font:{size:10} }, ticks:{font:{size:9}} }
    }
  }
});
const rl=document.getElementById('risk-legend');
[['#1565C0','Paludisme'],['#B71C1C','Rage/MPox'],['#006064','Leptospirose'],['#4A148C','Choléra'],['#E65100','Influenza av.'],['#546E7A','IRA/TB']].forEach(([c,l])=>{
  rl.innerHTML+=`<span style="display:flex;align-items:center;gap:3px;"><span style="width:9px;height:9px;border-radius:50%;background:${c};display:inline-block;"></span>${l}</span>`;
});

</script>

</div>
<div id="module-madsur" class="sbesoh-module" style="display:none;">

<style>
*{box-sizing:border-box;margin:0;padding:0;}
.app{font-family:var(--font-sans);background:var(--color-background-tertiary);}
.topbar{background:#0F1F5C;color:#fff;padding:9px 16px;display:flex;align-items:center;justify-content:space-between;}
.badge-oh{background:#C9A84C;color:#0F1F5C;font-size:10px;font-weight:500;padding:2px 7px;border-radius:4px;}
.tb-right{display:flex;align-items:center;gap:12px;font-size:11px;opacity:.8;}
.sdot{width:7px;height:7px;border-radius:50%;background:#4ade80;display:inline-block;margin-right:4px;}
.nav{background:var(--color-background-primary);border-bottom:.5px solid var(--color-border-tertiary);display:flex;padding:0 16px;overflow-x:auto;}
.ntab{padding:9px 13px;font-size:12px;cursor:pointer;border-bottom:2px solid transparent;color:var(--color-text-secondary);white-space:nowrap;display:flex;align-items:center;gap:5px;}
.ntab.active{border-bottom-color:#0F1F5C;color:var(--color-text-primary);font-weight:500;}
.ntab:hover:not(.active){background:var(--color-background-secondary);color:var(--color-text-primary);}
.content{padding:14px 16px;}
.card{background:var(--color-background-primary);border:.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-lg);padding:12px 14px;margin-bottom:12px;}
.ct{font-size:12px;font-weight:500;color:var(--color-text-primary);margin-bottom:10px;display:flex;align-items:center;justify-content:space-between;}
.ct-l{display:flex;align-items:center;gap:6px;}
.two{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:12px;}
.three{display:grid;grid-template-columns:1fr 1fr 1fr;gap:10px;margin-bottom:12px;}
.tab-content{display:none;}.tab-content.active{display:block;}
.krow{display:grid;grid-template-columns:repeat(auto-fit,minmax(130px,1fr));gap:9px;margin-bottom:14px;}
.kpi{background:var(--color-background-primary);border:.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-md);padding:10px 12px;}
.kl{font-size:10px;color:var(--color-text-secondary);margin-bottom:3px;}
.kv{font-size:20px;font-weight:500;line-height:1.1;}
.ks{font-size:10px;color:var(--color-text-secondary);margin-top:2px;}
.up{color:#E65100;}.dn{color:#1B5E20;}
.btn-s{background:var(--color-background-primary);border:.5px solid var(--color-border-secondary);border-radius:var(--border-radius-md);padding:5px 10px;font-size:11px;cursor:pointer;display:flex;align-items:center;gap:4px;color:var(--color-text-primary);}
.btn-s:hover{background:var(--color-background-secondary);}
.btn-p{background:#0F1F5C;color:#fff;border:none;border-radius:var(--border-radius-md);padding:6px 12px;font-size:11px;cursor:pointer;display:flex;align-items:center;gap:4px;}
.btn-p:hover{opacity:.9;}
.madsur-tr{cursor:pointer;transition:background .1s;}
.madsur-tr:hover{background:var(--color-background-info) !important;}
.madsur-tr.selected{background:#E6F1FB !important;outline:1.5px solid #0F1F5C;}
.d2a-panel{background:var(--color-background-secondary);border:.5px solid var(--color-border-secondary);border-radius:var(--border-radius-lg);padding:14px 16px;margin-top:12px;}
.d2a-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:12px;flex-wrap:wrap;gap:8px;}
.d2a-title{font-size:13px;font-weight:500;display:flex;align-items:center;gap:7px;}
.d2a-grid{display:grid;grid-template-columns:1fr 1fr 1fr;gap:10px;margin-bottom:12px;}
.d2a-block{background:var(--color-background-primary);border-radius:var(--border-radius-md);padding:10px 12px;border:.5px solid var(--color-border-tertiary);}
.d2a-block-title{font-size:10px;font-weight:500;color:var(--color-text-secondary);margin-bottom:5px;display:flex;align-items:center;gap:4px;}
.d2a-block-body{font-size:11px;line-height:1.6;}
.d2a-actions{display:flex;flex-direction:column;gap:6px;}
.action-item{display:flex;align-items:flex-start;gap:8px;padding:8px 10px;border-radius:var(--border-radius-md);border-left:3px solid;}
.action-item-label{font-size:10px;font-weight:500;margin-bottom:2px;}
.action-item-text{font-size:11px;}
.risk-meter{display:flex;align-items:center;gap:8px;padding:8px 10px;border-radius:var(--border-radius-md);margin-bottom:10px;}
.risk-bar-wrap{flex:1;height:8px;background:var(--color-background-secondary);border-radius:4px;overflow:hidden;}
.risk-bar{height:100%;border-radius:4px;transition:width .5s;}
.strebian-row{display:flex;align-items:center;gap:8px;padding:6px 9px;border-radius:var(--border-radius-md);background:var(--color-background-primary);font-size:11px;margin-bottom:5px;border:.5px solid var(--color-border-tertiary);}
.progress-ring{position:relative;display:inline-flex;align-items:center;justify-content:center;}
</style>

<h2 class="sr-only">SBESOH MADSUR — Module DataToAction : analyse intégrée signaux animaux</h2>

<div class="app">
  <div class="topbar">
    <div style="display:flex;align-items:center;gap:9px;">
      <span class="badge-oh">ONE HEALTH</span>
      <div>
        <div style="font-size:13px;font-weight:500;">SBESOH — MADSUR Surveillance · Signaux animaux & DataToAction</div>
        <div style="font-size:11px;opacity:.6;">DSV/MAEP · DVSSER · FHI360 STRIDES · SE 22 / 2026</div>
      </div>
    </div>
    <div class="tb-right"><span><span class="sdot"></span>Pipeline actif</span><span><i class="ti ti-calendar" aria-hidden="true"></i> SE 22</span></div>
  </div>

  <div class="nav">
    <div class="ntab active" onclick="showTabMADSUR('madsur',this)"><i class="ti ti-pig" aria-hidden="true"></i>MADSUR animal <span style="background:#006064;color:#fff;font-size:9px;padding:1px 5px;border-radius:3px;margin-left:3px;">23</span></div>
    <div class="ntab" onclick="showTabMADSUR('strebian',this)"><i class="ti ti-flask" aria-hidden="true"></i>STREBIAN / Labo <span id="str-badge" style="background:#B71C1C;color:#fff;font-size:9px;padding:1px 5px;border-radius:3px;margin-left:3px;">1 POSITIF</span></div>
    <div class="ntab" onclick="showTabMADSUR('zoonose',this)"><i class="ti ti-virus" aria-hidden="true"></i>Indice zoonose</div>
    <div class="ntab" onclick="showTabMADSUR('suivi',this)"><i class="ti ti-chart-line" aria-hidden="true"></i>Suivi hebdo</div>
  </div>

  <div class="content">

    <!-- MADSUR -->
    <div id="tab-madsur" class="tab-content active">
      <div class="krow">
        <div class="kpi"><div class="kl">Signaux reçus SE22</div><div class="kv" style="color:#006064;">23</div><div class="ks">3 régions connectées</div></div>
        <div class="kpi"><div class="kl">Espèces concernées</div><div class="kv">4</div><div class="ks">Bovins · Porcins · Volailles · Caprins</div></div>
        <div class="kpi"><div class="kl">Signaux zoonoses</div><div class="kv" style="color:#B71C1C;">2</div><div class="ks">Croisement SIMR actif</div></div>
        <div class="kpi"><div class="kl">Régions sans données</div><div class="kv" style="color:#F57F17;">19</div><div class="ks">sur 22 — Phase 1 pilote</div></div>
      </div>

      <div class="card">
        <div class="ct">
          <div class="ct-l"><i class="ti ti-table" style="color:#006064" aria-hidden="true"></i>Données MADSUR — Signaux SE 22 <span style="font-size:10px;color:var(--color-text-secondary);font-weight:400;margin-left:6px;">Cliquer une ligne pour l'analyse DataToAction</span></div>
        </div>
        <div style="overflow-x:auto;">
          <table style="width:100%;border-collapse:collapse;font-size:11px;">
            <thead><tr style="border-bottom:.5px solid var(--color-border-tertiary);">
              <th style="text-align:left;padding:5px 8px;font-weight:500;color:var(--color-text-secondary);">Région</th>
              <th style="text-align:left;padding:5px 8px;font-weight:500;color:var(--color-text-secondary);">Espèce</th>
              <th style="text-align:left;padding:5px 8px;font-weight:500;color:var(--color-text-secondary);">Syndrome</th>
              <th style="text-align:center;padding:5px 8px;font-weight:500;color:var(--color-text-secondary);">Cas</th>
              <th style="text-align:center;padding:5px 8px;font-weight:500;color:var(--color-text-secondary);">Décès anim.</th>
              <th style="text-align:center;padding:5px 8px;font-weight:500;color:var(--color-text-secondary);">% Troupeau</th>
              <th style="text-align:center;padding:5px 8px;font-weight:500;color:var(--color-text-secondary);">Risque zoonose</th>
              <th style="text-align:center;padding:5px 8px;font-weight:500;color:var(--color-text-secondary);">Croisement SIMR</th>
            </tr></thead>
            <tbody id="madsur-tbody"></tbody>
          </table>
        </div>

        <!-- PANNEAU DataToAction — apparaît après clic -->
        <div class="d2a-panel" id="d2a-panel" style="display:none;">
          <div class="d2a-header">
            <div class="d2a-title">
              <i class="ti ti-arrows-cross" style="color:#0F1F5C;font-size:16px;" aria-hidden="true"></i>
              <span id="d2a-title-text">DataToAction</span>
              <span id="d2a-level-badge"></span>
            </div>
            <div style="display:flex;gap:7px;">
              <button class="btn-s" id="d2a-close" onclick="closeD2A()"><i class="ti ti-x" aria-hidden="true"></i> Fermer</button>
            </div>
          </div>

          <!-- Indicateurs clés du signal sélectionné -->
          <div id="d2a-kpis" style="display:grid;grid-template-columns:repeat(auto-fit,minmax(110px,1fr));gap:8px;margin-bottom:12px;"></div>

          <!-- Barre de risque -->
          <div id="d2a-risk-bar" style="margin-bottom:12px;"></div>

          <!-- 3 blocs analyse -->
          <div class="d2a-grid" id="d2a-blocks"></div>

          <!-- Actions recommandées -->
          <div style="font-size:12px;font-weight:500;color:var(--color-text-primary);margin-bottom:7px;display:flex;align-items:center;gap:6px;">
            <i class="ti ti-list-check" style="color:#0F1F5C;" aria-hidden="true"></i>
            Actions recommandées — DataToAction
          </div>
          <div class="d2a-actions" id="d2a-actions"></div>

          <!-- Graphique tendance du signal -->
          <div style="margin-top:12px;">
            <div style="font-size:11px;font-weight:500;color:var(--color-text-secondary);margin-bottom:6px;">Tendance du signal — SE 18–22</div>
            <div style="position:relative;height:110px;"><canvas id="d2a-trend-chart" role="img" aria-label="Tendance du signal animal sélectionné"></canvas></div>
          </div>
        </div>
      </div>
    </div>

    <!-- STREBIAN -->
    <div id="tab-strebian" class="tab-content">
      <div class="krow">
        <div class="kpi"><div class="kl">Échantillons SE22</div><div class="kv">14</div><div class="ks">Reçus au laboratoire</div></div>
        <div class="kpi"><div class="kl">Résultats rendus</div><div class="kv">9</div><div class="ks">TAT médian : 8.3j</div></div>
        <div class="kpi"><div class="kl">POSITIFS</div><div class="kv" style="color:#B71C1C;">1</div><div class="ks">Rage bovine STR-0442</div></div>
        <div class="kpi"><div class="kl">En attente</div><div class="kv" style="color:#E65100;">5</div><div class="ks">Dont 2 zoonoses prioritaires</div></div>
      </div>
      <div class="card">
        <div class="ct"><div class="ct-l"><i class="ti ti-flask" style="color:#C9A84C" aria-hidden="true"></i>Suivi échantillons STREBIAN — SE 22</div></div>
        <div id="strebian-list"></div>
      </div>
      <div class="card">
        <div class="ct"><div class="ct-l"><i class="ti ti-chart-bar" style="color:#006064" aria-hidden="true"></i>TAT par agent pathogène (jours)</div></div>
        <div style="position:relative;height:160px;"><canvas id="tat-chart" role="img" aria-label="Délai TAT par test STREBIAN">Brucellose 3j, Rage 5j, Influenza 8j, Charbon 6j, PPA 9j</canvas></div>
      </div>
    </div>

    <!-- INDICE ZOONOSE -->
    <div id="tab-zoonose" class="tab-content">
      <div class="card">
        <div class="ct"><div class="ct-l"><i class="ti ti-virus" style="color:#B71C1C" aria-hidden="true"></i>Indice de risque zoonose par région — SE 22</div></div>
        <div style="display:flex;flex-direction:column;gap:7px;" id="zoonose-index"></div>
      </div>
      <div class="two">
        <div class="card">
          <div class="ct"><div class="ct-l"><i class="ti ti-chart-bar" style="color:#B71C1C" aria-hidden="true"></i>Score zoonose — composantes</div></div>
          <div style="position:relative;height:180px;"><canvas id="zoonose-radar" role="img" aria-label="Composantes score zoonose par région">Signal animal, signal humain, STREBIAN, convergence spatiale</canvas></div>
        </div>
        <div class="card">
          <div class="ct"><div class="ct-l"><i class="ti ti-info-circle" style="color:#0F1F5C" aria-hidden="true"></i>Calcul de l'indice</div></div>
          <div style="font-size:11px;line-height:1.7;color:var(--color-text-primary);">
            <div style="font-weight:500;margin-bottom:6px;">Formule : IZ = (SA × 0.30) + (SH × 0.30) + (CS × 0.20) + (STR × 0.20)</div>
            <div style="display:flex;flex-direction:column;gap:4px;">
              <div style="display:flex;gap:6px;"><span style="background:#E6F1FB;color:#0F1F5C;font-size:9px;padding:1px 6px;border-radius:3px;flex-shrink:0;">SA 30%</span><span>Signal animal — gravité syndrome + mortalité + % troupeau atteint</span></div>
              <div style="display:flex;gap:6px;"><span style="background:#FFEBEE;color:#B71C1C;font-size:9px;padding:1px 6px;border-radius:3px;flex-shrink:0;">SH 30%</span><span>Signal humain SIMR — cas inexpliqués, fièvre, même zone géographique</span></div>
              <div style="display:flex;gap:6px;"><span style="background:#E0F7FA;color:#006064;font-size:9px;padding:1px 6px;border-radius:3px;flex-shrink:0;">CS 20%</span><span>Convergence spatiale — distance fokontany animal vs humain ≤ 10 km</span></div>
              <div style="display:flex;gap:6px;"><span style="background:#FFF9C4;color:#F57F17;font-size:9px;padding:1px 6px;border-radius:3px;flex-shrink:0;">STR 20%</span><span>Résultat STREBIAN — positif = score max, en attente = 0.5, négatif = 0</span></div>
            </div>
            <div style="margin-top:8px;padding:7px 9px;background:var(--color-background-secondary);border-radius:var(--border-radius-md);">
              <div style="font-size:10px;color:var(--color-text-secondary);">Seuils d'alerte :</div>
              <div style="display:flex;gap:8px;margin-top:4px;flex-wrap:wrap;">
                <span style="font-size:10px;background:#FFCDD2;color:#B71C1C;padding:2px 7px;border-radius:3px;">IZ ≥ 0.7 — ROUGE</span>
                <span style="font-size:10px;background:#FFE0B2;color:#E65100;padding:2px 7px;border-radius:3px;">0.5–0.7 — ORANGE</span>
                <span style="font-size:10px;background:#FFF9C4;color:#F57F17;padding:2px 7px;border-radius:3px;">0.3–0.5 — JAUNE</span>
                <span style="font-size:10px;background:#E8F5E9;color:#1B5E20;padding:2px 7px;border-radius:3px;">&lt; 0.3 — VERT</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- SUIVI HEBDO -->
    <div id="tab-suivi" class="tab-content">
      <div class="card">
        <div class="ct"><div class="ct-l"><i class="ti ti-chart-line" style="color:#006064" aria-hidden="true"></i>Évolution signaux MADSUR — SE 18–22</div></div>
        <div style="position:relative;height:200px;"><canvas id="suivi-chart" role="img" aria-label="Évolution signaux MADSUR par espèce SE18-22">Bovins, Volailles, Porcins, Caprins</canvas></div>
        <div style="display:flex;gap:14px;flex-wrap:wrap;margin-top:8px;font-size:11px;color:var(--color-text-secondary);">
          <span><span style="display:inline-block;width:9px;height:9px;background:#006064;border-radius:2px;margin-right:3px;"></span>Bovins</span>
          <span><span style="display:inline-block;width:9px;height:9px;background:#C9A84C;border-radius:2px;margin-right:3px;"></span>Volailles</span>
          <span><span style="display:inline-block;width:9px;height:9px;background:#4A148C;border-radius:2px;margin-right:3px;"></span>Porcins</span>
          <span><span style="display:inline-block;width:9px;height:9px;background:#546E7A;border-radius:2px;margin-right:3px;"></span>Caprins</span>
        </div>
      </div>
      <div class="card">
        <div class="ct"><div class="ct-l"><i class="ti ti-target" style="color:#C9A84C" aria-hidden="true"></i>Couverture MADSUR — Objectif Phase 1</div></div>
        <div style="display:flex;flex-direction:column;gap:8px;" id="coverage-progress"></div>
      </div>
    </div>

  </div>
</div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.js"></script>
<script>
function showTabMADSUR(id, el) {
  document.querySelectorAll('.tab-content').forEach(t => t.classList.remove('active'));
  document.querySelectorAll('.ntab').forEach(t => t.classList.remove('active'));
  document.getElementById('tab-' + id).classList.add('active');
  el.classList.add('active');
}

// ── DONNÉES MADSUR ──────────────────────────────────────────────────────────
const madsurData = [
  {
    id:'MAD-01', region:'Analamanga', espece:'Bovins', syndrome:'Fièvre hémorragique + mortalité', cas:12, deces:3, pct:'8%', pctVal:8,
    zoonose:'SUSPECTE', zColor:'#B71C1C', zBg:'#FFCDD2', simr:'Oui (4 cas fièvre)', simrHot:true,
    iz:0.85, izLevel:'ROUGE',
    detail:{
      sa:0.90, sh:0.80, cs:0.85, str:0.80,
      analyse_animal:'Mortalité 8% en 48h. 12 bovins atteints sur 150 (3 fokontany: Amboatany, Tsaramasoandro, Mahitsy-Nord). Signes cliniques: hyperthermie 41°C, écoulements nasaux hémorragiques, décubitus latéral.',
      analyse_humain:'4 cas de fièvre indéterminée ≥ 38.5°C sur même fokontany dans les 14 jours. 1 cas mordu par un bovin présentant des signes neurologiques — prophylaxie post-exposition initiée.',
      analyse_env:'Zone d\'élevage extensif dense. Interface bovins–chiens errants–humains. Source d\'eau partagée bétail-population identifiée (Lac Masay). Accès vétérinaire limité.',
      strebian:'STR-0441 (brucellose) : en attente (J3). STR-0442 (rage sérologie) : POSITIF (J5). Prélèvement supplémentaire STR-0448 envoyé pour confirmation PCR rage.',
      tendance:[3,5,4,8,12],
      actions:[
        { prio:'IMMÉDIAT', color:'#B71C1C', bg:'#FFEBEE', text:'Activer équipe investigation One Health mixte DVSSER+DSV+GIV — déploiement Anjozorobe dans les 24h.' },
        { prio:'URGENT (48h)', color:'#E65100', bg:'#FFF3E0', text:'Lancer campagne vaccination antirabique d\'urgence pour les chiens du district Anjozorobe (estimé 2 000 chiens).' },
        { prio:'URGENT (48h)', color:'#E65100', bg:'#FFF3E0', text:'Identifier et suivre tous les contacts du cas mordu — prophylaxie post-exposition pour tout contact muqueux/cutané.' },
        { prio:'7 JOURS', color:'#F57F17', bg:'#FFFDE7', text:'Interdire temporairement le déplacement des bovins du district — prévention diffusion. Notifier OIE/WAHIS.' },
        { prio:'NOTIFICATION', color:'#4A148C', bg:'#F3E5F5', text:'Transmettre notification IHR à OMS pour cas rage humaine. Notification Africa CDC pour signal zoonose One Health.' },
      ]
    }
  },
  {
    id:'MAD-02', region:'Boeny', espece:'Bovins', syndrome:'Diarrhée hémorragique', cas:18, deces:1, pct:'3%', pctVal:3,
    zoonose:'Faible', zColor:'#F57F17', zBg:'#FFF9C4', simr:'Surveiller', simrHot:false,
    iz:0.42, izLevel:'JAUNE',
    detail:{
      sa:0.45, sh:0.30, cs:0.55, str:0.20,
      analyse_animal:'18 bovins diarrhée hémorragique sur 3 élevages du même périmètre irrigué. Mortalité 1 animal. Contexte : post-inondations mai 2026, eau de surface consommée directement.',
      analyse_humain:'89 cas GEA humains Boeny dont 18 pédiatriques — même zone géographique que les bovins atteints. Pas de lien causal confirmé. Suspicion contamination eau commune.',
      analyse_env:'Inondations inhabituelles mai 2026 (+40% précipitations vs normale). Points d\'eau communautaires non chlorés. Rizières inondées adjacentes aux enclos bovins.',
      strebian:'STR-0444 culture charbon : NÉGATIF. Pas d\'agent zoonose identifié. Prélèvement eau en attente (MEEF).',
      tendance:[4,5,8,10,18],
      actions:[
        { prio:'URGENT (48h)', color:'#E65100', bg:'#FFF3E0', text:'Chloration d\'urgence des 6 points d\'eau communautaires identifiés sur les 3 fokontany affectés.' },
        { prio:'7 JOURS', color:'#F57F17', bg:'#FFFDE7', text:'Prélèvements eau pour analyse microbiologique (E.coli, Leptospira) — MEEF + RESAMAD.' },
        { prio:'7 JOURS', color:'#F57F17', bg:'#FFFDE7', text:'Surveillance renforcée GEA humains Boeny — écouvillons copro sur 5 cas pédiatriques pour identification agent.' },
        { prio:'30 JOURS', color:'#006064', bg:'#E0F7FA', text:'Évaluation système d\'abreuvement bovin — séparer points d\'eau bétail et humains dans les élevages riverains.' },
      ]
    }
  },
  {
    id:'MAD-03', region:'Boeny', espece:'Volailles', syndrome:'Chute ponte + mortalité', cas:230, deces:45, pct:'12%', pctVal:12,
    zoonose:'Influenza ?', zColor:'#E65100', zBg:'#FFE0B2', simr:'Non', simrHot:false,
    iz:0.55, izLevel:'ORANGE',
    detail:{
      sa:0.75, sh:0.10, cs:0.40, str:0.50,
      analyse_animal:'230 volailles atteintes (poulets de chair et pondeuses) sur 4 exploitations dans rayon 8 km. Mortalité 45 oiseaux (20%). Syndrome : chute ponte brutale, dépression, mortalité subite. Aucun signe respiratoire marqué.',
      analyse_humain:'0 cas humains respiratoires ou fébriles signalés dans la zone. Éleveurs en bonne santé. Pas de croisement SIMR actuel.',
      analyse_env:'4 exploitations avicoles intensives à proximité d\'une zone humide (lac de retenue). Oiseaux sauvages migrateurs observés en grande quantité (pélicans, hérons). Saison migratoire actuelle.',
      strebian:'STR-0443 PCR Influenza A H5 : EN COURS (J8 — résultat attendu vendredi 29/05). STR-0447 sérologie H9 : envoyé J-1.',
      tendance:[40,60,90,140,230],
      actions:[
        { prio:'IMMÉDIAT', color:'#B71C1C', bg:'#FFEBEE', text:'Mesures de biosécurité renforcées : isolement des 4 exploitations, restriction mouvements volailles, EPI éleveurs (masques, gants).' },
        { prio:'URGENT (48h)', color:'#E65100', bg:'#FFF3E0', text:'Attendre résultat STR-0443 avant dépeuplement. Si H5 confirmé : activation protocole Influenza Aviaire Hautement Pathogène (IAHP).' },
        { prio:'URGENT (48h)', color:'#E65100', bg:'#FFF3E0', text:'Surveillance active symptômes IRA/fièvre chez les 23 éleveurs et travailleurs des 4 exploitations — signalement immédiat DRSP Boeny.' },
        { prio:'7 JOURS', color:'#F57F17', bg:'#FFFDE7', text:'Éloigner les volailles de la zone humide. Évaluer restriction accès oiseaux sauvages aux exploitations.' },
      ]
    }
  },
  {
    id:'MAD-04', region:'Atsinanana', espece:'Volailles', syndrome:'Chute ponte', cas:140, deces:8, pct:'4%', pctVal:4,
    zoonose:'Faible', zColor:'#F57F17', zBg:'#FFF9C4', simr:'Non', simrHot:false,
    iz:0.28, izLevel:'VERT',
    detail:{
      sa:0.30, sh:0.05, cs:0.20, str:0.10,
      analyse_animal:'140 pondeuses : chute ponte de 80% à 45% en 2 semaines. 8 décès (5%). Pas de mortalité subite. Syndrome compatible avec stress thermique ou carence alimentaire. Aucun signe systémique grave.',
      analyse_humain:'Aucun signal SIMR correspondant. Zone non priorisée.',
      analyse_env:'Forte chaleur inhabituelles avril-mai 2026 en côte Est. Coïncide avec chute ponte. Élevages en bâtiment ouvert sans ventilation.',
      strebian:'Non initié — risque zoonose faible. À surveiller si aggravation.',
      tendance:[120,130,125,138,140],
      actions:[
        { prio:'30 JOURS', color:'#006064', bg:'#E0F7FA', text:'Évaluation nutritionnelle et thermique des élevages affectés. Recommandation vétérinaire DSV.' },
        { prio:'SURVEILLANCE', color:'#546E7A', bg:'var(--color-background-secondary)', text:'Maintenir surveillance passive. Initier prélèvements si mortalité > 10% ou signes respiratoires.' },
      ]
    }
  },
  {
    id:'MAD-05', region:'Vakinankaratra', espece:'Porcins', syndrome:'Diarrhée + retard croissance', cas:24, deces:2, pct:'5%', pctVal:5,
    zoonose:'Non', zColor:'#1B5E20', zBg:'#E8F5E9', simr:'Non', simrHot:false,
    iz:0.20, izLevel:'VERT',
    detail:{
      sa:0.30, sh:0.05, cs:0.15, str:0.05,
      analyse_animal:'24 porcelets diarrhée + retard croissance sur 2 élevages familiaux. 2 décès. Syndrome évocateur PPA (Peste Porcine Africaine) ou diarrhée néonatale bactérienne. Pas de mortalité adulte.',
      analyse_humain:'Aucun croisement SIMR. PPA : pas de transmission humaine.',
      analyse_env:'Élevages familiaux semi-extensifs. Accès à des déchets organiques et à des eaux de ruissellement.',
      strebian:'STR-0445 ELISA PPA : EN COURS (J9). Résultat critique — PPA notifiable OIE si positif.',
      tendance:[5,8,12,18,24],
      actions:[
        { prio:'ATTENTE RÉSULTAT', color:'#E65100', bg:'#FFF3E0', text:'Résultat STR-0445 PPA attendu. Si positif : quarantaine stricte, notification OIE, plan d\'abattage selon protocole.' },
        { prio:'7 JOURS', color:'#F57F17', bg:'#FFFDE7', text:'Interdire provisoirement le déplacement des porcs de ces 2 élevages dans l\'attente du résultat PPA.' },
      ]
    }
  },
  {
    id:'MAD-06', region:'Vakinankaratra', espece:'Bovins', syndrome:'Boiterie + hyperthermie', cas:9, deces:0, pct:'2%', pctVal:2,
    zoonose:'Fièvre apht.?', zColor:'#E65100', zBg:'#FFE0B2', simr:'Non', simrHot:false,
    iz:0.35, izLevel:'JAUNE',
    detail:{
      sa:0.35, sh:0.05, cs:0.25, str:0.50,
      analyse_animal:'9 bovins boiterie sévère + hyperthermie 40.5°C + lésions vésiculaires pédi-interdigitées et buccales suspectées. Évocateur fièvre aphteuse (FA) — maladie OIE liste A.',
      analyse_humain:'FA : transmission humaine rarissime. Pas de signal SIMR correspondant.',
      analyse_env:'Zone d\'élevage intensif Vakinankaratra. Transhumance récente signalée depuis district voisin (Betafo).',
      strebian:'STR-0446 sérologie FA : EN COURS. Si positif — notification OIE obligatoire, impact commerce bétail régional.',
      tendance:[2,3,4,6,9],
      actions:[
        { prio:'URGENT (48h)', color:'#E65100', bg:'#FFF3E0', text:'Isoler les 9 bovins affectés. Restriction mouvements bétail du fokontany. Désinfection enclos.' },
        { prio:'ATTENTE RÉSULTAT', color:'#E65100', bg:'#FFF3E0', text:'Si STR-0446 FA positif : notification OIE/WAHIS obligatoire. Enquête épidémiologique traçabilité bétail (transhumance).' },
        { prio:'7 JOURS', color:'#F57F17', bg:'#FFFDE7', text:'Vaccination préventive du troupeau voisin si confirmation FA. Coordination avec Direction Régionale DSV Vakinankaratra.' },
      ]
    }
  },
  {
    id:'MAD-07', region:'Sofia', espece:'Caprins', syndrome:'Boiterie + plaies buccales', cas:15, deces:1, pct:'3%', pctVal:3,
    zoonose:'Non', zColor:'#1B5E20', zBg:'#E8F5E9', simr:'Non', simrHot:false,
    iz:0.18, izLevel:'VERT',
    detail:{
      sa:0.25, sh:0.02, cs:0.10, str:0.05,
      analyse_animal:'15 caprins boiterie + lésions buccales vésiculaires. 1 décès. Compatible ecthyma contagieux (orf) ou PPCB. Pas de signe systémique grave. Surveillance passive maintenue.',
      analyse_humain:'Orf : transmission humaine possible par contact direct. Recommander gants aux éleveurs.',
      analyse_env:'Troupeau transhumant. Contact récent avec troupeau inconnu signalé par l\'éleveur (marché Antsohihy).',
      strebian:'Non initié. À envisager si aggravation.',
      tendance:[3,5,7,9,15],
      actions:[
        { prio:'30 JOURS', color:'#006064', bg:'#E0F7FA', text:'Recommandation hygiène éleveurs (gants, lavage mains). Surveillance passive semaine suivante.' },
        { prio:'SURVEILLANCE', color:'#546E7A', bg:'var(--color-background-secondary)', text:'Initier STREBIAN si > 20% troupeau atteint ou propagation à nouveaux troupeaux.' },
      ]
    }
  },
  {
    id:'MAD-08', region:'Betsiboka', espece:'Bovins', syndrome:'RAS — surveillance passive', cas:2, deces:0, pct:'<1%', pctVal:0.5,
    zoonose:'Non', zColor:'#1B5E20', zBg:'#E8F5E9', simr:'Non', simrHot:false,
    iz:0.08, izLevel:'VERT',
    detail:{
      sa:0.05, sh:0.02, cs:0.10, str:0.00,
      analyse_animal:'2 bovins symptômes mineurs, résolution spontanée. Surveillance passive — aucun signal d\'alerte.',
      analyse_humain:'Pas de croisement SIMR. Zone de surveillance normale.',
      analyse_env:'Zone pastorale. Situation normale pour la saison.',
      strebian:'Non initié.',
      tendance:[3,4,2,3,2],
      actions:[
        { prio:'SURVEILLANCE', color:'#546E7A', bg:'var(--color-background-secondary)', text:'Maintenir surveillance passive. Rapport MADSUR hebdomadaire suffisant.' },
      ]
    }
  },
  {
    id:'MAD-09', region:"Amoron'i Mania", espece:'Bovins', syndrome:'Fièvre aphtose suspectée', cas:7, deces:0, pct:'1%', pctVal:1,
    zoonose:'Faible', zColor:'#F57F17', zBg:'#FFF9C4', simr:'Non', simrHot:false,
    iz:0.25, izLevel:'VERT',
    detail:{
      sa:0.25, sh:0.02, cs:0.20, str:0.30,
      analyse_animal:'7 bovins lésions buccales légères + boiterie discrète. Compatible FA stade précoce ou lésions traumatiques. Éleveur incertain du diagnostic.',
      analyse_humain:'Pas de signal SIMR. FA : transmission humaine rarissime.',
      analyse_env:'Élevage extensif montagnard. Transhumance possible depuis Vakinankaratra — à vérifier (lien potentiel MAD-06).',
      strebian:'Non initié. Mise en observation 7 jours.',
      tendance:[1,2,3,5,7],
      actions:[
        { prio:'7 JOURS', color:'#F57F17', bg:'#FFFDE7', text:'Observation active 7 jours. Vérifier lien épidémiologique avec le signal MAD-06 Vakinankaratra (transhumance).' },
        { prio:'7 JOURS', color:'#F57F17', bg:'#FFFDE7', text:'Initier STR si aggravation ou confirmation lésions vésiculaires typiques FA.' },
      ]
    }
  },
  {
    id:'MAD-10', region:'Sava', espece:'Volailles', syndrome:'Surveillance passive RAS', cas:3, deces:0, pct:'<1%', pctVal:0.3,
    zoonose:'Non', zColor:'#1B5E20', zBg:'#E8F5E9', simr:'Non', simrHot:false,
    iz:0.06, izLevel:'VERT',
    detail:{
      sa:0.05, sh:0.02, cs:0.05, str:0.00,
      analyse_animal:'3 volailles symptômes mineurs. Pas de signal d\'alerte. Situation normale.',
      analyse_humain:'Aucun croisement.',
      analyse_env:'Zone côtière SAVA. Surveillance saisonnière standard.',
      strebian:'Non initié.',
      tendance:[4,3,4,3,3],
      actions:[
        { prio:'SURVEILLANCE', color:'#546E7A', bg:'var(--color-background-secondary)', text:'Rapport MADSUR hebdomadaire suffisant. Surveiller oiseaux migrateurs (lien MAD-03 Boeny influenza).' },
      ]
    }
  },
];

// ── RENDU TABLE MADSUR ───────────────────────────────────────────────────────
const tbody = document.getElementById('madsur-tbody');
let selectedId = null;
let trendChart = null;

madsurData.forEach((row, i) => {
  const tr = document.createElement('tr');
  tr.className = 'madsur-tr';
  tr.style = `border-bottom:.5px solid var(--color-border-tertiary);${i%2===0?'background:var(--color-background-secondary);':''}`;
  const izBg = { ROUGE:'#FFCDD2', ORANGE:'#FFE0B2', JAUNE:'#FFF9C4', VERT:'#E8F5E9' };
  const izTxt = { ROUGE:'#B71C1C', ORANGE:'#E65100', JAUNE:'#F57F17', VERT:'#1B5E20' };
  tr.innerHTML = `
    <td style="padding:5px 8px;font-weight:500;">${row.region}</td>
    <td style="padding:5px 8px;">${row.espece}</td>
    <td style="padding:5px 8px;">${row.syndrome}</td>
    <td style="text-align:center;padding:5px 8px;font-weight:500;font-size:13px;">${row.cas}</td>
    <td style="text-align:center;padding:5px 8px;">${row.deces}</td>
    <td style="text-align:center;padding:5px 8px;font-weight:500;color:${row.pctVal>=8?'#B71C1C':row.pctVal>=5?'#E65100':'var(--color-text-primary)'};">${row.pct}</td>
    <td style="text-align:center;padding:5px 8px;"><span style="background:${row.zBg};color:${row.zColor};font-size:9px;padding:1px 6px;border-radius:3px;font-weight:500;">${row.zoonose}</span></td>
    <td style="text-align:center;padding:5px 8px;"><span style="background:${row.simrHot?'#FFCDD2':'var(--color-background-secondary)'};color:${row.simrHot?'#B71C1C':'var(--color-text-secondary)'};font-size:9px;padding:1px 6px;border-radius:3px;">${row.simr}</span></td>`;
  tr.addEventListener('click', () => openD2A(row, tr));
  tbody.appendChild(tr);
});

function openD2A(row, tr) {
  // Highlight selected row
  document.querySelectorAll('.madsur-tr').forEach(r => r.classList.remove('selected'));
  tr.classList.add('selected');
  selectedId = row.id;

  const d = row.detail;
  const izColors = { ROUGE:'#B71C1C', ORANGE:'#E65100', JAUNE:'#F57F17', VERT:'#1B5E20' };
  const izBgs = { ROUGE:'#FFCDD2', ORANGE:'#FFE0B2', JAUNE:'#FFF9C4', VERT:'#E8F5E9' };
  const c = izColors[row.izLevel];

  document.getElementById('d2a-title-text').textContent = `${row.id} — ${row.region} · ${row.espece} · ${row.syndrome}`;
  document.getElementById('d2a-level-badge').innerHTML = `<span style="background:${izBgs[row.izLevel]};color:${c};font-size:10px;padding:2px 8px;border-radius:3px;font-weight:500;">IZ = ${row.iz.toFixed(2)} — ${row.izLevel}</span>`;

  // KPIs
  document.getElementById('d2a-kpis').innerHTML = `
    <div style="background:var(--color-background-primary);border:.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-md);padding:8px 10px;"><div style="font-size:10px;color:var(--color-text-secondary);">Cas animaux</div><div style="font-size:17px;font-weight:500;">${row.cas}</div></div>
    <div style="background:var(--color-background-primary);border:.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-md);padding:8px 10px;"><div style="font-size:10px;color:var(--color-text-secondary);">Décès</div><div style="font-size:17px;font-weight:500;">${row.deces}</div></div>
    <div style="background:var(--color-background-primary);border:.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-md);padding:8px 10px;"><div style="font-size:10px;color:var(--color-text-secondary);">% Troupeau</div><div style="font-size:17px;font-weight:500;color:${row.pctVal>=8?'#B71C1C':row.pctVal>=5?'#E65100':'var(--color-text-primary)'};">${row.pct}</div></div>
    <div style="background:${izBgs[row.izLevel]};border:.5px solid ${c};border-radius:var(--border-radius-md);padding:8px 10px;"><div style="font-size:10px;color:${c};font-weight:500;">Indice zoonose</div><div style="font-size:17px;font-weight:500;color:${c};">${row.iz.toFixed(2)}</div></div>`;

  // Barre de risque
  document.getElementById('d2a-risk-bar').innerHTML = `
    <div style="display:flex;align-items:center;gap:10px;padding:8px 10px;background:${izBgs[row.izLevel]};border-radius:var(--border-radius-md);border:.5px solid ${c}33;">
      <div style="font-size:11px;font-weight:500;color:${c};width:80px;flex-shrink:0;">Risque ${row.izLevel}</div>
      <div style="flex:1;height:10px;background:rgba(0,0,0,0.08);border-radius:5px;overflow:hidden;"><div style="height:100%;width:${Math.round(row.iz*100)}%;background:${c};border-radius:5px;transition:width .6s;"></div></div>
      <div style="font-size:12px;font-weight:500;color:${c};width:35px;text-align:right;">${Math.round(row.iz*100)}%</div>
    </div>`;

  // 3 blocs analyse
  document.getElementById('d2a-blocks').innerHTML = `
    <div class="d2a-block">
      <div class="d2a-block-title" style="color:#006064;"><i class="ti ti-pig" aria-hidden="true"></i>Signal animal (SA = ${d.sa.toFixed(2)})</div>
      <div class="d2a-block-body">${d.analyse_animal}</div>
    </div>
    <div class="d2a-block">
      <div class="d2a-block-title" style="color:#B71C1C;"><i class="ti ti-user" aria-hidden="true"></i>Signal humain (SH = ${d.sh.toFixed(2)})</div>
      <div class="d2a-block-body">${d.analyse_humain}</div>
    </div>
    <div class="d2a-block">
      <div class="d2a-block-title" style="color:#546E7A;"><i class="ti ti-trees" aria-hidden="true"></i>Environnement (CS = ${d.cs.toFixed(2)})</div>
      <div class="d2a-block-body">${d.analyse_env}</div>
    </div>
    <div class="d2a-block" style="grid-column:span 3;">
      <div class="d2a-block-title" style="color:#C9A84C;"><i class="ti ti-flask" aria-hidden="true"></i>STREBIAN (STR = ${d.str.toFixed(2)})</div>
      <div class="d2a-block-body">${d.strebian}</div>
    </div>`;

  // Actions
  const actEl = document.getElementById('d2a-actions');
  actEl.innerHTML = '';
  d.actions.forEach(a => {
    actEl.innerHTML += `<div style="display:flex;align-items:flex-start;gap:8px;padding:8px 10px;border-radius:var(--border-radius-md);background:${a.bg};border-left:3px solid ${a.color};border:.5px solid ${a.color}33;border-left-width:3px;">
      <span style="background:${a.color};color:#fff;font-size:9px;padding:2px 6px;border-radius:3px;font-weight:500;white-space:nowrap;flex-shrink:0;">${a.prio}</span>
      <span style="font-size:11px;">${a.text}</span>
    </div>`;
  });

  // Graphique tendance
  if (trendChart) { trendChart.destroy(); trendChart = null; }
  setTimeout(() => {
    const ctx = document.getElementById('d2a-trend-chart');
    trendChart = new Chart(ctx, {
      type:'line',
      data:{
        labels:['SE18','SE19','SE20','SE21','SE22'],
        datasets:[{ label:'Cas animaux', data:d.tendance, borderColor:c, backgroundColor:c+'22', fill:true, tension:0.3, pointBackgroundColor:c, pointRadius:4 }]
      },
      options:{ responsive:true, maintainAspectRatio:false, plugins:{legend:{display:false}},
        scales:{ x:{ticks:{font:{size:10},autoSkip:false}}, y:{ticks:{font:{size:10}},beginAtZero:true} } }
    });
  }, 50);

  document.getElementById('d2a-panel').style.display = 'block';
  document.getElementById('d2a-panel').scrollIntoView({ behavior:'smooth', block:'nearest' });
}

function closeD2A() {
  document.getElementById('d2a-panel').style.display = 'none';
  document.querySelectorAll('.madsur-tr').forEach(r => r.classList.remove('selected'));
  if (trendChart) { trendChart.destroy(); trendChart = null; }
  selectedId = null;
}

// ── STREBIAN ─────────────────────────────────────────────────────────────────
const strebianData = [
  { id:'STR-0441', region:'Analamanga', espece:'Bovin', test:'PCR Brucellose', statut:'En attente', tat:3, resultat:'-', prio:'HAUTE' },
  { id:'STR-0442', region:'Analamanga', espece:'Bovin', test:'Sérologie Rage', statut:'Positif', tat:5, resultat:'POSITIF', prio:'CRITIQUE' },
  { id:'STR-0443', region:'Boeny', espece:'Volaille', test:'PCR Influenza A H5', statut:'En cours', tat:8, resultat:'-', prio:'HAUTE' },
  { id:'STR-0444', region:'Boeny', espece:'Bovin', test:'Culture Charbon', statut:'Négatif', tat:6, resultat:'Négatif', prio:'MODÉRÉE' },
  { id:'STR-0445', region:'Vakinankaratra', espece:'Porc', test:'ELISA PPA', statut:'En cours', tat:9, resultat:'-', prio:'HAUTE' },
  { id:'STR-0446', region:'Vakinankaratra', espece:'Bovin', test:'Sérologie FA', statut:'En cours', tat:4, resultat:'-', prio:'HAUTE' },
  { id:'STR-0447', region:'Boeny', espece:'Volaille', test:'Sérologie H9N2', statut:'En cours', tat:1, resultat:'-', prio:'MODÉRÉE' },
  { id:'STR-0448', region:'Analamanga', espece:'Bovin', test:'PCR Rage (confirmation)', statut:'En cours', tat:1, resultat:'-', prio:'CRITIQUE' },
];
const strEl = document.getElementById('strebian-list');
const sBg2 = { CRITIQUE:'#FFCDD2', HAUTE:'#FFE0B2', MODÉRÉE:'#FFF9C4' };
const sTxt2 = { CRITIQUE:'#B71C1C', HAUTE:'#E65100', MODÉRÉE:'#F57F17' };
strebianData.forEach((s, i) => {
  const rBg = s.resultat==='POSITIF'?'#FFCDD2':s.statut==='En attente'||s.statut==='En cours'?'#FFE0B2':'#E8F5E9';
  const rTxt = s.resultat==='POSITIF'?'#B71C1C':s.statut==='En attente'||s.statut==='En cours'?'#E65100':'#1B5E20';
  strEl.innerHTML += `<div style="display:flex;align-items:center;gap:8px;padding:7px 9px;background:${i%2===0?'var(--color-background-secondary)':'var(--color-background-primary)'};border-radius:var(--border-radius-md);font-size:11px;margin-bottom:4px;border:.5px solid var(--color-border-tertiary);">
    <span style="font-family:var(--font-mono);font-size:10px;color:var(--color-text-secondary);flex-shrink:0;">${s.id}</span>
    <span style="flex:1;">${s.region} — ${s.test} (${s.espece})</span>
    <span style="color:var(--color-text-secondary);font-size:10px;">TAT ${s.tat}j</span>
    <span style="background:${sBg2[s.prio]||'#E8F5E9'};color:${sTxt2[s.prio]||'#1B5E20'};font-size:9px;padding:1px 6px;border-radius:3px;">${s.prio}</span>
    <span style="background:${rBg};color:${rTxt};font-size:9px;padding:2px 7px;border-radius:3px;font-weight:500;">${s.resultat!=='-'?s.resultat:s.statut}</span>
  </div>`;
});

new Chart(document.getElementById('tat-chart'), {
  type:'bar',
  data:{ labels:['PCR Brucellose\n(STR-0441)','Rage\n(STR-0442)','Influen. A H5\n(STR-0443)','Charbon\n(STR-0444)','ELISA PPA\n(STR-0445)','Séro FA\n(STR-0446)'],
    datasets:[
      { label:'TAT actuel (j)', data:[3,5,8,6,9,4], backgroundColor:['#FFE0B2','#FFCDD2','#FFE0B2','#E8F5E9','#FFE0B2','#FFE0B2'] },
      { label:'Cible ≤7j', data:[7,7,7,7,7,7], type:'line', borderColor:'#1B5E20', borderDash:[4,3], pointRadius:0, fill:false },
    ] },
  options:{ responsive:true, maintainAspectRatio:false, plugins:{legend:{display:false}},
    scales:{ x:{ticks:{font:{size:9},autoSkip:false}}, y:{ticks:{font:{size:9}},max:12, title:{display:true,text:'Jours',font:{size:9}}} } }
});

// ── INDICE ZOONOSE ───────────────────────────────────────────────────────────
const zRegions = [
  { region:'Analamanga (MAD-01)', iz:0.85, sa:0.90, sh:0.80, cs:0.85, str:0.80, level:'ROUGE' },
  { region:'Boeny — Volailles (MAD-03)', iz:0.55, sa:0.75, sh:0.10, cs:0.40, str:0.50, level:'ORANGE' },
  { region:'Boeny — Bovins (MAD-02)', iz:0.42, sa:0.45, sh:0.30, cs:0.55, str:0.20, level:'JAUNE' },
  { region:'Vakinankaratra — FA (MAD-06)', iz:0.35, sa:0.35, sh:0.05, cs:0.25, str:0.50, level:'JAUNE' },
  { region:"Amoron'i Mania (MAD-09)", iz:0.25, sa:0.25, sh:0.02, cs:0.20, str:0.30, level:'VERT' },
  { region:'Vakinankaratra — Porcins (MAD-05)', iz:0.20, sa:0.30, sh:0.05, cs:0.15, str:0.05, level:'VERT' },
  { region:'Sofia (MAD-07)', iz:0.18, sa:0.25, sh:0.02, cs:0.10, str:0.05, level:'VERT' },
  { region:'Betsiboka (MAD-08)', iz:0.08, sa:0.05, sh:0.02, cs:0.10, str:0.00, level:'VERT' },
];
const izColors2 = { ROUGE:'#B71C1C', ORANGE:'#E65100', JAUNE:'#F57F17', VERT:'#1B5E20' };
const izBgs2 = { ROUGE:'#FFCDD2', ORANGE:'#FFE0B2', JAUNE:'#FFF9C4', VERT:'#E8F5E9' };
const zEl = document.getElementById('zoonose-index');
zRegions.forEach(z => {
  const c = izColors2[z.level];
  zEl.innerHTML += `<div style="display:flex;align-items:center;gap:10px;padding:8px 10px;background:var(--color-background-primary);border-radius:var(--border-radius-md);border:.5px solid var(--color-border-tertiary);">
    <span style="font-size:11px;flex:1;font-weight:${z.iz>=0.5?'500':'400'};">${z.region}</span>
    <div style="display:flex;gap:5px;font-size:9px;">
      <span style="background:#E6F1FB;color:#0F1F5C;padding:1px 5px;border-radius:3px;">SA ${z.sa.toFixed(2)}</span>
      <span style="background:#FFEBEE;color:#B71C1C;padding:1px 5px;border-radius:3px;">SH ${z.sh.toFixed(2)}</span>
      <span style="background:#E0F7FA;color:#006064;padding:1px 5px;border-radius:3px;">CS ${z.cs.toFixed(2)}</span>
      <span style="background:#FFF9C4;color:#F57F17;padding:1px 5px;border-radius:3px;">STR ${z.str.toFixed(2)}</span>
    </div>
    <div style="width:80px;height:8px;background:var(--color-background-secondary);border-radius:4px;overflow:hidden;flex-shrink:0;">
      <div style="height:100%;width:${Math.round(z.iz*100)}%;background:${c};border-radius:4px;"></div>
    </div>
    <span style="background:${izBgs2[z.level]};color:${c};font-size:10px;padding:2px 8px;border-radius:3px;font-weight:500;width:52px;text-align:center;flex-shrink:0;">${z.iz.toFixed(2)}</span>
  </div>`;
});

new Chart(document.getElementById('zoonose-radar'), {
  type:'bar',
  data:{
    labels:['Analamanga','Boeny V.','Boeny B.','Vaki FA','Amoro.','Vaki P.','Sofia','Betsi.'],
    datasets:[
      { label:'SA Signal animal', data:[0.90,0.75,0.45,0.35,0.25,0.30,0.25,0.05], backgroundColor:'rgba(0,96,100,0.7)' },
      { label:'SH Signal humain', data:[0.80,0.10,0.30,0.05,0.02,0.05,0.02,0.02], backgroundColor:'rgba(183,28,28,0.7)' },
      { label:'STR STREBIAN', data:[0.80,0.50,0.20,0.50,0.30,0.05,0.05,0.00], backgroundColor:'rgba(201,168,76,0.7)' },
    ]
  },
  options:{ responsive:true, maintainAspectRatio:false, plugins:{legend:{labels:{font:{size:9},boxWidth:10}}},
    scales:{ x:{stacked:true,ticks:{font:{size:8},autoSkip:false}}, y:{stacked:true,max:1,ticks:{font:{size:9}}} } }
});

// ── SUIVI HEBDO ───────────────────────────────────────────────────────────────
new Chart(document.getElementById('suivi-chart'), {
  type:'line',
  data:{
    labels:['SE18','SE19','SE20','SE21','SE22'],
    datasets:[
      { label:'Bovins', data:[8,9,11,12,11], borderColor:'#006064', backgroundColor:'rgba(0,96,100,0.07)', fill:true, tension:0.3, pointRadius:4 },
      { label:'Volailles', data:[2,3,5,5,6], borderColor:'#C9A84C', backgroundColor:'rgba(201,168,76,0.07)', fill:true, tension:0.3, pointRadius:4 },
      { label:'Porcins', data:[1,2,2,3,4], borderColor:'#4A148C', backgroundColor:'rgba(74,20,140,0.07)', fill:true, tension:0.3, pointRadius:4 },
      { label:'Caprins', data:[1,1,2,2,3], borderColor:'#546E7A', backgroundColor:'rgba(84,110,122,0.07)', fill:true, tension:0.3, pointRadius:4 },
    ]
  },
  options:{ responsive:true, maintainAspectRatio:false, plugins:{legend:{display:false}},
    scales:{ x:{ticks:{font:{size:10},autoSkip:false}}, y:{ticks:{font:{size:10}}} } }
});

const targets = [
  { label:'Régions connectées MADSUR', current:3, target:22, color:'#006064' },
  { label:'Signaux hebdomadaires', current:23, target:80, color:'#0F1F5C' },
  { label:'Espèces surveillées', current:4, target:6, color:'#C9A84C' },
  { label:'STREBIAN TAT ≤ 7j', current:4, target:8, color:'#1B5E20' },
];
const covEl = document.getElementById('coverage-progress');
targets.forEach(t => {
  const pct = Math.round(t.current/t.target*100);
  covEl.innerHTML += `<div>
    <div style="display:flex;justify-content:space-between;font-size:11px;margin-bottom:4px;">
      <span>${t.label}</span>
      <span style="font-weight:500;">${t.current} / ${t.target} <span style="color:var(--color-text-secondary);">(${pct}%)</span></span>
    </div>
    <div style="height:8px;background:var(--color-background-secondary);border-radius:4px;overflow:hidden;">
      <div style="height:100%;width:${pct}%;background:${t.color};border-radius:4px;transition:width .5s;"></div>
    </div>
  </div>`;
});
</script>

</div>

<div id="module-carto" class="sbesoh-module" style="display:none;">

<style>
.carto-app{font-family:var(--font-sans);background:var(--color-background-tertiary);min-height:calc(100vh - 48px);}
.carto-topbar{background:linear-gradient(135deg,#0F1F5C 0%,#1a3480 100%);color:#fff;padding:10px 18px;display:flex;align-items:center;justify-content:space-between;gap:12px;}
.carto-tb-title{font-size:13px;font-weight:600;letter-spacing:.2px;}
.carto-tb-sub{font-size:10px;opacity:.65;margin-top:1px;}
.carto-krow{display:grid;grid-template-columns:repeat(auto-fit,minmax(120px,1fr));gap:9px;padding:12px 16px 0;}
.carto-kpi{background:#fff;border:.5px solid var(--color-border-tertiary);border-radius:8px;padding:10px 12px;}
.carto-kl{font-size:10px;color:var(--color-text-secondary);margin-bottom:3px;}
.carto-kv{font-size:20px;font-weight:600;line-height:1.1;}
.carto-ks{font-size:10px;color:var(--color-text-secondary);margin-top:2px;}
.carto-body{display:grid;grid-template-columns:minmax(240px,380px) 1fr;gap:12px;padding:12px 16px;}
.carto-left{}
.carto-right{display:flex;flex-direction:column;gap:12px;}
.carto-card{background:#fff;border:.5px solid var(--color-border-tertiary);border-radius:10px;padding:12px 14px;}
.carto-ct{font-size:12px;font-weight:500;color:var(--color-text-primary);margin-bottom:10px;display:flex;align-items:center;justify-content:space-between;}
.carto-ct-l{display:flex;align-items:center;gap:6px;}
.carto-filter-row{display:flex;gap:6px;margin-bottom:10px;flex-wrap:wrap;align-items:center;padding:0 16px;}
.carto-filter-btn{padding:4px 11px;font-size:11px;border:.5px solid var(--color-border-secondary);border-radius:20px;cursor:pointer;background:#fff;color:var(--color-text-secondary);display:flex;align-items:center;gap:4px;transition:all .12s;}
.carto-filter-btn:hover{background:var(--color-background-secondary);}
.carto-filter-btn.active{background:#0F1F5C;color:#fff;border-color:#0F1F5C;}
.carto-filter-btn.active-teal{background:#006064;color:#fff;border-color:#006064;}
.carto-filter-btn.active-red{background:#B71C1C;color:#fff;border-color:#B71C1C;}
.map-legend-h{display:flex;flex-wrap:wrap;gap:7px;margin-top:8px;}
.leg-item-h{display:flex;align-items:center;gap:4px;font-size:10px;color:var(--color-text-secondary);}
.leg-sq-h{width:11px;height:11px;border-radius:2px;}
.region-info-box{font-size:12px;color:var(--color-text-secondary);}
.carto-table{width:100%;border-collapse:collapse;font-size:11px;}
.carto-table th{text-align:left;padding:5px 8px;font-weight:500;color:var(--color-text-secondary);border-bottom:.5px solid var(--color-border-tertiary);}
.carto-table td{padding:5px 8px;border-bottom:.5px solid var(--color-border-tertiary);}
.carto-table tr:nth-child(even){background:var(--color-background-secondary);}
.carto-badge{font-size:9px;padding:2px 7px;border-radius:3px;font-weight:500;}
@media(max-width:700px){.carto-body{grid-template-columns:1fr;}}
</style>

<div class="carto-app">
  <div class="carto-topbar">
    <div>
      <div class="carto-tb-title"><i class="ti ti-map-2" style="margin-right:6px"></i>SBESOH — Cartographie One Health · SE 22</div>
      <div class="carto-tb-sub">SIMR humain + MADSUR animal + Alertes · 22 régions · Madagascar</div>
    </div>
    <div style="display:flex;gap:8px;align-items:center;">
      <span style="background:#C9A84C;color:#0F1F5C;font-size:10px;font-weight:600;padding:2px 8px;border-radius:4px;">ONE HEALTH</span>
      <span style="font-size:10px;opacity:.7;">28/05/2026 · SE 22</span>
    </div>
  </div>

  <div class="carto-krow">
    <div class="carto-kpi"><div class="carto-kl">Régions surveillées</div><div class="carto-kv">22</div><div class="carto-ks">sur 22 — couverture nationale</div></div>
    <div class="carto-kpi"><div class="carto-kl">Régions ROUGE/ORANGE</div><div class="carto-kv" style="color:#E65100;">6</div><div class="carto-ks">27% du territoire</div></div>
    <div class="carto-kpi"><div class="carto-kl">Signaux MADSUR actifs</div><div class="carto-kv" style="color:#006064;">23</div><div class="carto-ks">7 régions avec ≥1 signal</div></div>
    <div class="carto-kpi"><div class="carto-kl">Convergence OH détectée</div><div class="carto-kv" style="color:#B71C1C;">3</div><div class="carto-ks">Zones humain + animal</div></div>
    <div class="carto-kpi"><div class="carto-kl">Complétude rapportage</div><div class="carto-kv">76%</div><div class="carto-ks">6 SDSP non déclarants</div></div>
  </div>

  <div style="height:10px;"></div>

  <div class="carto-filter-row">
    <span style="font-size:11px;color:var(--color-text-secondary);font-weight:500;">Couche :</span>
    <button class="carto-filter-btn active" id="cf-humain" onclick="setCartoFilter('humain')"><i class="ti ti-user" aria-hidden="true"></i> Cas humains SIMR</button>
    <button class="carto-filter-btn" id="cf-maladie" onclick="setCartoFilter('maladie')"><i class="ti ti-virus" aria-hidden="true"></i> Maladie dominante</button>
    <button class="carto-filter-btn" id="cf-animal" onclick="setCartoFilter('animal')"><i class="ti ti-pig" aria-hidden="true"></i> MADSUR signaux</button>
    <button class="carto-filter-btn" id="cf-alerte" onclick="setCartoFilter('alerte')"><i class="ti ti-bell" aria-hidden="true"></i> Alerte OH</button>
    <button class="carto-filter-btn" id="cf-completude" onclick="setCartoFilter('completude')"><i class="ti ti-clipboard-check" aria-hidden="true"></i> Complétude</button>
  </div>

  <div class="carto-body">
    <div class="carto-left">
      <div class="carto-card" style="padding:10px;">
        <div class="carto-ct">
          <div class="carto-ct-l"><i class="ti ti-map" style="color:#0F1F5C"></i>Madagascar — 22 régions</div>
          <span id="carto-mode-label" style="font-size:10px;color:var(--color-text-secondary);">Cas humains SIMR</span>
        </div>
        <div id="carto-map-container"></div>
        <div class="map-legend-h" id="carto-map-legend"></div>
      </div>
    </div>

    <div class="carto-right">
      <div class="carto-card">
        <div class="carto-ct">
          <div class="carto-ct-l"><i class="ti ti-info-circle" style="color:#0F1F5C"></i><span id="carto-region-title">Sélectionner une région</span></div>
        </div>
        <div id="carto-region-detail" class="region-info-box">
          Cliquez une région sur la carte pour voir le détail One Health — signaux SIMR humains, animaux MADSUR, statut STREBIAN et niveau d'alerte.
        </div>
      </div>

      <div class="carto-card">
        <div class="carto-ct"><div class="carto-ct-l"><i class="ti ti-alert-triangle" style="color:#B71C1C"></i>Zones de convergence One Health — SE 22</div></div>
        <div style="display:flex;flex-direction:column;gap:7px;" id="carto-convergence-list">
          <div style="background:#FFEBEE;border:.5px solid #EF9F9F;border-radius:6px;padding:9px 11px;">
            <div style="font-size:12px;font-weight:500;color:#B71C1C;margin-bottom:3px;"><i class="ti ti-arrow-right"></i> Analamanga — Rage + MPox</div>
            <div style="font-size:11px;color:var(--color-text-secondary);">SIM-01 rage humaine (3 cas, 1 décès) + MAD-01 rage bovine (IZ=0.85) · Foyer confirmé Anjozorobe · Riposte GIV+MSANP active</div>
            <div style="margin-top:4px;display:flex;gap:5px;">
              <span class="carto-badge" style="background:#B71C1C;color:#fff;">ROUGE</span>
              <span class="carto-badge" style="background:#FFCDD2;color:#B71C1C;">Zoonose confirmée</span>
              <span class="carto-badge" style="background:#E6F1FB;color:#0F1F5C;">Riposte J3</span>
            </div>
          </div>
          <div style="background:#FFF3E0;border:.5px solid #FBBF85;border-radius:6px;padding:9px 11px;">
            <div style="font-size:12px;font-weight:500;color:#E65100;margin-bottom:3px;"><i class="ti ti-arrow-right"></i> Boeny — Paludisme + Influenza aviaire + Leptospirose</div>
            <div style="font-size:11px;color:var(--color-text-secondary);">SIM-03+SIM-06 (humains) + MAD-02+MAD-03 (animaux) · Triple signal SIMR+MADSUR+Environnement · Zone inondable → risque amplifié</div>
            <div style="margin-top:4px;display:flex;gap:5px;">
              <span class="carto-badge" style="background:#E65100;color:#fff;">ORANGE</span>
              <span class="carto-badge" style="background:#FFE0B2;color:#E65100;">Triple OH</span>
            </div>
          </div>
          <div style="background:#FFF3E0;border:.5px solid #FBBF85;border-radius:6px;padding:9px 11px;">
            <div style="font-size:12px;font-weight:500;color:#E65100;margin-bottom:3px;"><i class="ti ti-arrow-right"></i> Melaky — Anthrax suspect</div>
            <div style="font-size:11px;color:var(--color-text-secondary);">MAD-05 (3 zébus morts IZ=0.65) · Exposition humaine éleveurs possible · STR-0450 résultat urgent attendu</div>
            <div style="margin-top:4px;display:flex;gap:5px;">
              <span class="carto-badge" style="background:#E65100;color:#fff;">ORANGE</span>
              <span class="carto-badge" style="background:#FFE0B2;color:#E65100;">Résultat STR urgent</span>
            </div>
          </div>
        </div>
      </div>

      <div class="carto-card">
        <div class="carto-ct"><div class="carto-ct-l"><i class="ti ti-virus" style="color:#B71C1C"></i>MPox — Distribution géographique SE 22</div></div>
        <div id="carto-mpox-list" style="display:flex;flex-direction:column;gap:4px;">
          <div style="display:flex;align-items:center;gap:8px;padding:5px 8px;background:var(--color-background-secondary);border-radius:5px;font-size:11px;"><span style="font-weight:500;flex:1;">Analamanga</span><span style="font-weight:500;color:#B71C1C;">3 cas</span><span style="background:#FFCDD2;color:#B71C1C;font-size:9px;padding:1px 5px;border-radius:3px;">+1</span></div>
          <div style="font-size:10px;color:var(--color-text-secondary);padding:1px 8px 4px;">Marché Isotry — cluster identifié</div>
          <div style="display:flex;align-items:center;gap:8px;padding:5px 8px;border-radius:5px;font-size:11px;"><span style="font-weight:500;flex:1;">Boeny</span><span style="font-weight:500;color:#B71C1C;">2 cas</span><span style="background:#FFCDD2;color:#B71C1C;font-size:9px;padding:1px 5px;border-radius:3px;">+2</span></div>
          <div style="font-size:10px;color:var(--color-text-secondary);padding:1px 8px 4px;">Contact direct lésions actives confirmé</div>
          <div style="display:flex;align-items:center;gap:8px;padding:5px 8px;background:var(--color-background-secondary);border-radius:5px;font-size:11px;"><span style="font-weight:500;flex:1;">DIANA</span><span style="font-weight:500;color:#B71C1C;">1 cas</span><span style="background:#FFCDD2;color:#B71C1C;font-size:9px;padding:1px 5px;border-radius:3px;">Nouveau</span></div>
          <div style="font-size:10px;color:var(--color-text-secondary);padding:1px 8px 4px;">Retour voyage — cas index à identifier</div>
          <div style="display:flex;align-items:center;gap:8px;padding:5px 8px;border-radius:5px;font-size:11px;"><span style="font-weight:500;flex:1;">Atsinanana</span><span style="font-weight:500;color:#B71C1C;">1 cas</span><span style="background:#FFCDD2;color:#B71C1C;font-size:9px;padding:1px 5px;border-radius:3px;">Nouveau</span></div>
          <div style="font-size:10px;color:var(--color-text-secondary);padding:1px 8px 4px;">Professionnel de santé — EPI renforcé</div>
        </div>
      </div>

      <div class="carto-card">
        <div class="carto-ct"><div class="carto-ct-l"><i class="ti ti-clipboard-check" style="color:#006064"></i>Complétude rapportage SIMR — SE 22</div></div>
        <div id="carto-completude" style="display:flex;flex-direction:column;gap:5px;">
          <div style="font-size:11px;color:var(--color-text-secondary);margin-bottom:5px;">Districts rapportants / total · 22 régions</div>
          <script>
            (function(){
              const compl=[
                {r:'Analamanga',p:84},{r:'Boeny',p:78},{r:'Atsinanana',p:81},{r:'Vakinankaratra',p:72},
                {r:'Sofia',p:65},{r:'Sava',p:58},{r:'Diana',p:55},{r:'Haute Matsiatra',p:68},
                {r:'Alaotra-Mangoro',p:75},{r:'Analanjirofo',p:69},{r:'Bongolava',p:71},{r:'Itasy',p:76},
                {r:'Menabe',p:60},{r:'Melaky',p:52},{r:'Betsiboka',p:70},{r:"Amoron'i Mania",p:62},
                {r:'Atsimo-Andrefana',p:48},{r:'Anosy',p:54},{r:'Androy',p:43},{r:'Atsimo-Atsinanana',p:57},
                {r:'Ihorombe',p:45},{r:'Vatovavy',p:41}
              ];
              const el=document.getElementById('carto-completude');
              compl.forEach(c=>{
                const col=c.p>=75?'#1B5E20':c.p>=60?'#F57F17':'#B71C1C';
                const bg=c.p>=75?'#E8F5E9':c.p>=60?'#FFF9C4':'#FFEBEE';
                el.innerHTML+=`<div style="display:flex;align-items:center;gap:8px;">
                  <span style="font-size:10px;min-width:120px;color:var(--color-text-primary);">${c.r}</span>
                  <div style="flex:1;background:var(--color-background-tertiary);border-radius:3px;height:8px;overflow:hidden;">
                    <div style="width:${c.p}%;height:100%;background:${col};border-radius:3px;"></div>
                  </div>
                  <span style="font-size:10px;font-weight:500;color:${col};min-width:32px;text-align:right;">${c.p}%</span>
                </div>`;
              });
            })();
          </script>
        </div>
      </div>
    </div>
  </div>
</div>

<script>
// ── CARTE CARTOGRAPHIE ───────────────────────────────────────────────────────
let cartoMapDrawn = false;
let cartoSvgSel;
let cartoCurrentFilter = 'humain';

const cartoRegionData = {
  'Analamanga':      { cas:298, completude:84, madsur:5, alerte:'rouge',  mpox:3, lepto:8,  palu:12, maladie_dom:'Rage+MPox', madsur_signals:'MAD-01 Rage bovine (IZ=0.85) · Riposte active' },
  'Boeny':           { cas:312, completude:78, madsur:4, alerte:'orange', mpox:2, lepto:0,  palu:312, maladie_dom:'Paludisme', madsur_signals:'MAD-02 Leptospirose bovine · MAD-03 H5N1 volailles' },
  'Atsinanana':      { cas:187, completude:81, madsur:3, alerte:'jaune',  mpox:1, lepto:28, palu:0,  maladie_dom:'Leptospirose', madsur_signals:'STR-0445 leptospirose en cours' },
  'Vakinankaratra':  { cas:142, completude:72, madsur:4, alerte:'jaune',  mpox:0, lepto:0,  palu:0,  maladie_dom:'Brucellose/IRA', madsur_signals:'MAD-04 FMD bovine (45 cas)' },
  'Sofia':           { cas:89,  completude:65, madsur:3, alerte:'jaune',  mpox:0, lepto:0,  palu:42, maladie_dom:'Paludisme', madsur_signals:'Surveillance passive volailles' },
  'Betsiboka':       { cas:43,  completude:70, madsur:2, alerte:'vert',   mpox:0, lepto:0,  palu:18, maladie_dom:'Paludisme', madsur_signals:'Aucun signal actif' },
  'Alaotra-Mangoro': { cas:76,  completude:75, madsur:0, alerte:'vert',   mpox:0, lepto:0,  palu:5,  maladie_dom:'IRA', madsur_signals:'Non couvert' },
  'Haute Matsiatra': { cas:54,  completude:68, madsur:0, alerte:'vert',   mpox:0, lepto:0,  palu:0,  maladie_dom:'Tuberculose', madsur_signals:'Non couvert' },
  "Amoron'i Mania":  { cas:38,  completude:62, madsur:1, alerte:'jaune',  mpox:0, lepto:0,  palu:0,  maladie_dom:'GEA', madsur_signals:'Surveillance porcins' },
  'Diana':           { cas:61,  completude:55, madsur:0, alerte:'jaune',  mpox:1, lepto:0,  palu:0,  maladie_dom:'MPox+Dengue', madsur_signals:'Non couvert' },
  'Sava':            { cas:47,  completude:58, madsur:1, alerte:'vert',   mpox:0, lepto:12, palu:0,  maladie_dom:'Leptospirose', madsur_signals:'Surveillance rongeurs' },
  'Analanjirofo':    { cas:29,  completude:69, madsur:0, alerte:'vert',   mpox:0, lepto:14, palu:0,  maladie_dom:'Leptospirose', madsur_signals:'Non couvert' },
  'Bongolava':       { cas:22,  completude:71, madsur:0, alerte:'vert',   mpox:0, lepto:0,  palu:8,  maladie_dom:'Paludisme', madsur_signals:'Non couvert' },
  'Itasy':           { cas:31,  completude:76, madsur:0, alerte:'vert',   mpox:0, lepto:0,  palu:0,  maladie_dom:'IRA', madsur_signals:'Non couvert' },
  'Menabe':          { cas:19,  completude:60, madsur:0, alerte:'vert',   mpox:0, lepto:0,  palu:10, maladie_dom:'Paludisme', madsur_signals:'Non couvert' },
  'Melaky':          { cas:11,  completude:52, madsur:0, alerte:'jaune',  mpox:0, lepto:0,  palu:8,  maladie_dom:'Anthrax suspect', madsur_signals:'MAD-05 Anthrax zébus (IZ=0.65) STR URGENT' },
  'Atsimo-Andrefana':{ cas:33,  completude:48, madsur:0, alerte:'jaune',  mpox:0, lepto:0,  palu:0,  maladie_dom:'Données manquantes', madsur_signals:'Non couvert' },
  'Anosy':           { cas:15,  completude:54, madsur:0, alerte:'vert',   mpox:0, lepto:0,  palu:0,  maladie_dom:'GEA', madsur_signals:'Non couvert' },
  'Androy':          { cas:8,   completude:43, madsur:0, alerte:'jaune',  mpox:0, lepto:0,  palu:0,  maladie_dom:'Données manquantes', madsur_signals:'Non couvert' },
  'Atsimo-Atsinanana':{ cas:24, completude:57, madsur:0, alerte:'vert',   mpox:0, lepto:0,  palu:0,  maladie_dom:'Diarrhée', madsur_signals:'Non couvert' },
  'Ihorombe':        { cas:12,  completude:45, madsur:0, alerte:'jaune',  mpox:0, lepto:0,  palu:0,  maladie_dom:'Données manquantes', madsur_signals:'Non couvert' },
  'Vatovavy':        { cas:17,  completude:41, madsur:0, alerte:'jaune',  mpox:0, lepto:0,  palu:0,  maladie_dom:'Données manquantes', madsur_signals:'Non couvert' },
};

const cartoMaladieColors = {
  'Rage+MPox':'#B71C1C', 'MPox+Dengue':'#B71C1C', 'Paludisme':'#1565C0',
  'Leptospirose':'#006064', 'Brucellose/IRA':'#4A148C', 'Tuberculose':'#546E7A',
  'IRA':'#546E7A', 'GEA':'#558B2F', 'Diarrhée':'#558B2F',
  'Anthrax suspect':'#E65100', 'Données manquantes':'#B0B0B0',
};

function getCartoColor(name, filter) {
  const d = cartoRegionData[name];
  if (!d) return '#E0E0E0';
  if (filter === 'humain') {
    const v = d.cas;
    if (v>250) return '#0C447C'; if (v>150) return '#185FA5'; if (v>80) return '#378ADD';
    if (v>40) return '#85B7EB'; if (v>10) return '#B5D4F4'; return '#E6F1FB';
  }
  if (filter === 'maladie') return cartoMaladieColors[d.maladie_dom] || '#B0B0B0';
  if (filter === 'animal') {
    const v = d.madsur;
    if (v>=4) return '#085041'; if (v>=2) return '#1D9E75'; if (v>=1) return '#5DCAA5'; return '#E1F5EE';
  }
  if (filter === 'alerte') {
    if (d.alerte==='rouge') return '#B71C1C'; if (d.alerte==='orange') return '#E65100';
    if (d.alerte==='jaune') return '#F57F17'; return '#1B5E20';
  }
  if (filter === 'completude') {
    const v = d.completude;
    if (v>=80) return '#1B5E20'; if (v>=65) return '#4CAF50'; if (v>=50) return '#F57F17'; return '#B71C1C';
  }
  return '#E0E0E0';
}

function getCartoLegend(f) {
  if (f==='humain') return [['#0C447C','>250 cas'],['#378ADD','80–250'],['#85B7EB','40–80'],['#B5D4F4','10–40'],['#E6F1FB','<10']];
  if (f==='maladie') return [['#B71C1C','Rage/MPox'],['#1565C0','Paludisme'],['#006064','Leptospirose'],['#4A148C','Brucellose'],['#546E7A','IRA/TB'],['#E65100','Anthrax'],['#B0B0B0','Données manq.']];
  if (f==='animal') return [['#085041','≥4 signaux MADSUR'],['#1D9E75','2–3'],['#5DCAA5','1'],['#E1F5EE','Aucun']];
  if (f==='alerte') return [['#B71C1C','ROUGE'],['#E65100','ORANGE'],['#F57F17','JAUNE'],['#1B5E20','VERT']];
  if (f==='completude') return [['#1B5E20','≥80%'],['#4CAF50','65–79%'],['#F57F17','50–64%'],['#B71C1C','<50%']];
}

function setCartoFilter(f) {
  cartoCurrentFilter = f;
  document.querySelectorAll('.carto-filter-btn').forEach(b => { b.classList.remove('active', 'active-teal', 'active-red'); });
  document.getElementById('cf-'+f).classList.add('active');
  document.getElementById('carto-mode-label').textContent = {
    humain:'Cas humains SIMR', maladie:'Maladie dominante', animal:'MADSUR signaux', alerte:'Niveau alerte OH', completude:'Complétude rapportage'
  }[f];
  if (cartoSvgSel) cartoSvgSel.selectAll('path').attr('fill', d => getCartoColor(d.properties.name, cartoCurrentFilter));
  const leg = document.getElementById('carto-map-legend');
  leg.innerHTML = '';
  getCartoLegend(f).forEach(([c,l]) => { leg.innerHTML += `<div class="leg-item-h"><div class="leg-sq-h" style="background:${c}"></div>${l}</div>`; });
}

function drawCartoMap() {
  cartoMapDrawn = true;
  const container = document.getElementById('carto-map-container');
  const W = container.offsetWidth || 300, H = W * 2.0;
  const svg = d3.select('#carto-map-container').append('svg').attr('viewBox',`0 0 ${W} ${H}`).attr('width','100%').style('display','block');
  cartoSvgSel = svg;
  const tooltip = document.getElementById('map-tooltip');
  d3.json('https://cdn.jsdelivr.net/npm/datamaps@0.5.10/src/js/data/mdg.topo.json').then(topo => {
    const features = topojson.feature(topo, topo.objects.mdg).features;
    const proj = d3.geoMercator().fitSize([W,H], topojson.feature(topo, topo.objects.mdg));
    const path = d3.geoPath(proj);
    svg.selectAll('path').data(features).join('path')
      .attr('d', path).attr('stroke', '#fff').attr('stroke-width', 0.6)
      .attr('fill', d => getCartoColor(d.properties.name, cartoCurrentFilter)).attr('cursor', 'pointer')
      .on('mousemove', function(event, d) {
        const name = d.properties.name, rd = cartoRegionData[name];
        if (!rd) return;
        const ac = {rouge:'#B71C1C',orange:'#E65100',jaune:'#F57F17',vert:'#1B5E20'};
        const al = {rouge:'ROUGE',orange:'ORANGE',jaune:'JAUNE',vert:'VERT'};
        tooltip.innerHTML = `<div style="font-weight:500;margin-bottom:3px;">${name}</div>
          <div style="font-size:10px;color:var(--color-text-secondary);">Cas SIMR: <strong>${rd.cas}</strong> · MADSUR: <strong>${rd.madsur} signaux</strong></div>
          <div style="font-size:10px;">${rd.maladie_dom}</div>
          ${rd.mpox>0?`<div style="font-size:10px;color:#B71C1C;">MPox: <strong>${rd.mpox} cas</strong></div>`:''}
          <div style="margin-top:3px;"><span style="background:${ac[rd.alerte]};color:#fff;font-size:9px;padding:1px 6px;border-radius:3px;">${al[rd.alerte]}</span></div>`;
        tooltip.style.opacity = '1'; tooltip.style.left = (event.clientX+12)+'px'; tooltip.style.top = (event.clientY-10)+'px';
      })
      .on('mouseleave', () => { tooltip.style.opacity = '0'; })
      .on('click', function(event, d) {
        const name = d.properties.name, rd = cartoRegionData[name];
        if (!rd) return;
        const ac = {rouge:'#B71C1C',orange:'#E65100',jaune:'#F57F17',vert:'#1B5E20'};
        const ab = {rouge:'#FFEBEE',orange:'#FFF3E0',jaune:'#FFFDE7',vert:'#E8F5E9'};
        const al = {rouge:'ROUGE',orange:'ORANGE',jaune:'JAUNE',vert:'VERT'};
        document.getElementById('carto-region-title').textContent = name;
        document.getElementById('carto-region-detail').innerHTML = `
          <div style="display:flex;gap:5px;flex-wrap:wrap;margin-bottom:8px;">
            <span style="background:${ab[rd.alerte]};color:${ac[rd.alerte]};font-size:10px;padding:2px 8px;border-radius:3px;font-weight:500;">${al[rd.alerte]}</span>
            <span style="background:#E6F1FB;color:#0F1F5C;font-size:10px;padding:2px 8px;border-radius:3px;">${rd.maladie_dom}</span>
            <span style="background:#E0F7FA;color:#006064;font-size:10px;padding:2px 8px;border-radius:3px;">${rd.completude}% complétude</span>
          </div>
          <div style="display:grid;grid-template-columns:1fr 1fr;gap:5px;font-size:11px;margin-bottom:8px;">
            <div style="background:var(--color-background-secondary);border-radius:6px;padding:6px 8px;"><div style="color:var(--color-text-secondary);font-size:10px;">Cas SIMR humains</div><div style="font-size:16px;font-weight:600;">${rd.cas}</div></div>
            <div style="background:#E0F7FA;border-radius:6px;padding:6px 8px;"><div style="color:#006064;font-size:10px;">Signaux MADSUR</div><div style="font-size:16px;font-weight:600;color:#006064;">${rd.madsur}</div></div>
            ${rd.mpox>0?`<div style="background:#FFEBEE;border-radius:6px;padding:6px 8px;"><div style="color:#B71C1C;font-size:10px;font-weight:500;">MPox</div><div style="font-size:16px;font-weight:600;color:#B71C1C;">${rd.mpox}</div></div>`:''}
            ${rd.palu>0?`<div style="background:#E3F2FD;border-radius:6px;padding:6px 8px;"><div style="color:#1565C0;font-size:10px;font-weight:500;">Paludisme</div><div style="font-size:16px;font-weight:600;color:#1565C0;">${rd.palu}</div></div>`:''}
            ${rd.lepto>0?`<div style="background:#E0F7FA;border-radius:6px;padding:6px 8px;"><div style="color:#006064;font-size:10px;font-weight:500;">Leptospirose</div><div style="font-size:16px;font-weight:600;color:#006064;">${rd.lepto}</div></div>`:''}
          </div>
          <div style="background:var(--color-background-secondary);border-radius:6px;padding:7px 9px;font-size:11px;margin-bottom:6px;">
            <div style="font-size:10px;font-weight:500;color:#006064;margin-bottom:2px;"><i class="ti ti-pig"></i> MADSUR</div>
            <div>${rd.madsur_signals}</div>
          </div>
          <button class="btn-s" style="font-size:10px;" onclick="sendPrompt('Analyse One Health détaillée région ${name} SE22 Madagascar')">Analyse ${name} ↗</button>`;
        svg.selectAll('path').attr('stroke', '#fff').attr('stroke-width', 0.6);
        d3.select(this).attr('stroke', '#C9A84C').attr('stroke-width', 2);
      });
    setCartoFilter('humain');
  });
}

// Déclencher la carte quand le module est affiché
document.addEventListener('DOMContentLoaded', function() {
  // handled by switchModule
});
</script>

</div>

<div id="module-v5" class="sbesoh-module" style="display:none;">

<style>
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:'Anthropic Sans',sans-serif;background:transparent}
.hdr{background:#0F1F5C;color:#fff;padding:14px 20px;display:flex;align-items:center;justify-content:space-between;border-radius:var(--border-radius-lg) var(--border-radius-lg) 0 0}
.hdr-title{font-size:16px;font-weight:500;letter-spacing:.3px}
.hdr-sub{font-size:11px;opacity:.7}
.hdr-right{display:flex;gap:10px;align-items:center}
.badge-live{background:#C9A84C;color:#3a2800;font-size:10px;font-weight:500;padding:3px 8px;border-radius:20px}
.tabs{display:flex;border-bottom:1px solid var(--color-border-tertiary);background:var(--color-background-primary)}
.tab{padding:10px 18px;font-size:13px;color:var(--color-text-secondary);cursor:pointer;border-bottom:2px solid transparent;transition:all .2s;white-space:nowrap}
.tab.active{color:#0F1F5C;border-bottom-color:#C9A84C;font-weight:500}
.tab:hover:not(.active){background:var(--color-background-secondary)}
.tab-dot{display:inline-block;width:7px;height:7px;border-radius:50%;margin-right:5px}
.panel{display:none;padding:16px}
.panel.active{display:block}
.kpi-row{display:grid;grid-template-columns:repeat(4,1fr);gap:10px;margin-bottom:16px}
.kpi{background:var(--color-background-secondary);border-radius:var(--border-radius-md);padding:10px 12px}
.kpi-label{font-size:11px;color:var(--color-text-secondary);margin-bottom:4px}
.kpi-val{font-size:20px;font-weight:500;color:var(--color-text-primary)}
.kpi-trend{font-size:11px;margin-top:2px}
.up{color:#d32f2f}.dn{color:#388e3c}.st{color:#888}
.tbl-wrap{overflow-x:auto;border:0.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-md)}
table{width:100%;border-collapse:collapse;font-size:12px;table-layout:fixed}
th{background:var(--color-background-secondary);padding:8px 10px;text-align:left;font-weight:500;color:var(--color-text-secondary);font-size:11px;border-bottom:0.5px solid var(--color-border-tertiary)}
td{padding:8px 10px;border-bottom:0.5px solid var(--color-border-tertiary);color:var(--color-text-primary);vertical-align:middle}
tr:last-child td{border-bottom:none}
tr.clickable{cursor:pointer}
tr.clickable:hover td{background:var(--color-background-secondary)}
tr.selected td{background:#E8EDFF}
.pill{display:inline-block;padding:2px 8px;border-radius:20px;font-size:10px;font-weight:500}
.pill-r{background:#FCEBEB;color:#A32D2D}
.pill-o{background:#FAEEDA;color:#854F0B}
.pill-y{background:#FFFDE7;color:#7a6000}
.pill-g{background:#EAF3DE;color:#3B6D11}
.pill-b{background:#E6F1FB;color:#185FA5}
.dta-panel{margin-top:16px;border:1px solid #C9A84C;border-radius:var(--border-radius-md);overflow:hidden}
.dta-header{background:#0F1F5C;color:#fff;padding:10px 14px;display:flex;align-items:center;gap:8px;font-size:13px;font-weight:500}
.dta-header span{font-size:11px;opacity:.7;margin-left:auto}
.dta-body{padding:14px;background:var(--color-background-primary)}
.dta-kpis{display:grid;grid-template-columns:repeat(4,1fr);gap:8px;margin-bottom:14px}
.dta-kpi{background:var(--color-background-secondary);border-radius:var(--border-radius-md);padding:8px 10px;text-align:center}
.dta-kpi-lbl{font-size:10px;color:var(--color-text-secondary);margin-bottom:3px}
.dta-kpi-val{font-size:16px;font-weight:500}
.risk-bar-wrap{margin-bottom:14px}
.risk-label{font-size:11px;color:var(--color-text-secondary);margin-bottom:4px;display:flex;justify-content:space-between}
.risk-bar{height:10px;border-radius:5px;background:#eee;position:relative}
.risk-fill{height:100%;border-radius:5px;transition:width .5s}
.dta-grid{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:14px}
.dta-block{border:0.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-md);padding:10px 12px}
.dta-block-title{font-size:11px;font-weight:500;color:var(--color-text-secondary);margin-bottom:6px;display:flex;align-items:center;gap:5px}
.dta-block p{font-size:12px;color:var(--color-text-primary);line-height:1.5}
.dta-block .score{font-size:18px;font-weight:500;float:right}
.actions-title{font-size:11px;font-weight:500;color:var(--color-text-secondary);margin-bottom:8px}
.action-list{display:flex;flex-direction:column;gap:5px}
.action-item{display:flex;align-items:flex-start;gap:8px;padding:7px 10px;border-radius:var(--border-radius-md);font-size:11px}
.act-imm{background:#FCEBEB;border-left:3px solid #A32D2D}
.act-urg{background:#FAEEDA;border-left:3px solid #854F0B}
.act-7j{background:#FFF9C4;border-left:3px solid #7a6000}
.act-30j{background:#EAF3DE;border-left:3px solid #3B6D11}
.act-surv{background:#E6F1FB;border-left:3px solid #185FA5}
.act-tag{font-weight:500;min-width:70px}
.trend-mini{margin-top:14px;padding-top:12px;border-top:0.5px solid var(--color-border-tertiary)}
.trend-label{font-size:11px;color:var(--color-text-secondary);margin-bottom:8px}
.sect-title{font-size:13px;font-weight:500;color:var(--color-text-primary);margin-bottom:10px;margin-top:16px;display:flex;align-items:center;gap:6px}
.sect-title:first-child{margin-top:0}
.oh-grid{display:grid;grid-template-columns:1fr 1fr 1fr;gap:10px;margin-top:12px}
.oh-col{border:0.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-md);overflow:hidden}
.oh-col-hdr{padding:8px 12px;font-size:12px;font-weight:500;color:#fff}
.oh-col-body{padding:10px 12px}
.oh-item{padding:5px 0;border-bottom:0.5px solid var(--color-border-tertiary);font-size:11px;color:var(--color-text-primary)}
.oh-item:last-child{border-bottom:none}
.oh-badge{float:right;padding:1px 6px;border-radius:8px;font-size:10px}
.conv-card{border:0.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-md);padding:12px;margin-bottom:8px;display:flex;gap:12px;align-items:flex-start}
.conv-icon{width:36px;height:36px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:16px;flex-shrink:0}
.conv-body{flex:1}
.conv-title{font-size:13px;font-weight:500;color:var(--color-text-primary);margin-bottom:3px}
.conv-sub{font-size:11px;color:var(--color-text-secondary);line-height:1.5}
.conv-tags{margin-top:6px;display:flex;gap:5px;flex-wrap:wrap}
.close-btn{background:none;border:0.5px solid rgba(255,255,255,.4);color:#fff;padding:3px 10px;border-radius:20px;font-size:11px;cursor:pointer}
.close-btn:hover{background:rgba(255,255,255,.1)}
</style>

<h2 class="sr-only">Dashboard SBESOH — Surveillance One Health : flux SIMR humain et MADSUR animal avec module DataToAction</h2>

<div style="border:0.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-lg);overflow:hidden;background:var(--color-background-primary)">

<div class="hdr">
  <div>
    <div class="hdr-title"><i class="ti ti-shield-check" aria-hidden="true" style="margin-right:6px"></i>SBESOH — Intégré One Health · SIMR × MADSUR × Bulletin</div>
    <div class="hdr-sub">SE 22 · 2026 · Madagascar · FHI360/STRIDES</div>
  </div>
  <div class="hdr-right">
    <span class="badge-live"><i class="ti ti-circle-filled" style="font-size:8px;margin-right:3px"></i>LIVE</span>
    <span style="font-size:11px;opacity:.7">Dernière MAJ: 28/05/2026 06:00</span>
  </div>
</div>

<div class="tabs">
  <div class="tab active" onclick="showTabV5('simr',this)"><span class="tab-dot" style="background:#E53935"></span>SIMR Humain</div>
  <div class="tab" onclick="showTabV5('madsur',this)"><span class="tab-dot" style="background:#FB8C00"></span>MADSUR Animal</div>
  <div class="tab" onclick="showTabV5('oh',this)"><span class="tab-dot" style="background:#0F1F5C"></span>Convergence OH</div>
  <div class="tab" onclick="showTabV5('top5-oh',this)"><span class="tab-dot" style="background:#C9A84C"></span>Top 5 Prioritaires</div>
  <div class="tab" onclick="showTabV5('croisee-oh',this)"><span class="tab-dot" style="background:#B71C1C"></span>Analyse croisée</div>
  <div class="tab" onclick="showTabV5('bulletin',this)"><span class="tab-dot" style="background:#0F1F5C"></span>Bulletin SE 22</div>
</div>

<div id="tab-simr" class="panel active">
  <div class="kpi-row">
    <div class="kpi"><div class="kpi-label">Signaux actifs</div><div class="kpi-val" style="color:#E53935">12</div><div class="kpi-trend up">↑ 3 vs SE21</div></div>
    <div class="kpi"><div class="kpi-label">Alertes ROUGE</div><div class="kpi-val" style="color:#A32D2D">3</div><div class="kpi-trend up">Dont 1 MPox SE22</div></div>
    <div class="kpi"><div class="kpi-label">Délai détection moy.</div><div class="kpi-val" style="color:#0F1F5C">4.8j</div><div class="kpi-trend dn">↓ 0.4j vs cible 7j</div></div>
    <div class="kpi"><div class="kpi-label">Districts en riposte</div><div class="kpi-val" style="color:#185FA5">7</div><div class="kpi-trend st">Stable</div></div>
  </div>

  <div class="sect-title"><i class="ti ti-table" aria-hidden="true"></i>Signaux DHIS2/SIMR — Semaine 22 <span style="font-size:11px;color:var(--color-text-secondary);margin-left:auto">Cliquer une ligne → DataToAction</span></div>
  <div class="tbl-wrap">
    <table>
      <colgroup><col style="width:11%"><col style="width:16%"><col style="width:14%"><col style="width:9%"><col style="width:9%"><col style="width:9%"><col style="width:10%"><col style="width:10%"><col style="width:12%"></colgroup>
      <thead><tr>
        <th>Réf.</th><th>Maladie</th><th>Région</th><th>Cas</th><th>Décès</th><th>Tx Létalité</th><th>Tendance</th><th>Alerte</th><th>7-1-7</th>
      </tr></thead>
      <tbody id="simr-tbody"></tbody>
    </table>
  </div>
  <div id="simr-dta" style="display:none"></div>
</div>

<div id="tab-madsur" class="panel">
  <div class="kpi-row">
    <div class="kpi"><div class="kpi-label">Foyers animaux</div><div class="kpi-val" style="color:#FB8C00">10</div><div class="kpi-trend up">↑ 2 vs SE21</div></div>
    <div class="kpi"><div class="kpi-label">IZ ROUGE</div><div class="kpi-val" style="color:#A32D2D">2</div><div class="kpi-trend up">Rage + Influenza av.</div></div>
    <div class="kpi"><div class="kpi-label">Espèces affectées</div><div class="kpi-val" style="color:#0F1F5C">6</div><div class="kpi-trend st">Bovins, volailles, chiens...</div></div>
    <div class="kpi"><div class="kpi-label">STREBIAN positifs</div><div class="kpi-val" style="color:#185FA5">4</div><div class="kpi-trend up">↑ 1 vs SE21</div></div>
  </div>

  <div class="sect-title"><i class="ti ti-table" aria-hidden="true"></i>Signaux MADSUR — Semaine 22 <span style="font-size:11px;color:var(--color-text-secondary);margin-left:auto">Cliquer une ligne → DataToAction</span></div>
  <div class="tbl-wrap">
    <table>
      <colgroup><col style="width:11%"><col style="width:16%"><col style="width:13%"><col style="width:11%"><col style="width:9%"><col style="width:9%"><col style="width:8%"><col style="width:11%"><col style="width:12%"></colgroup>
      <thead><tr>
        <th>Réf.</th><th>Maladie/Agent</th><th>Région</th><th>Espèce</th><th>Cas anim.</th><th>Décès</th><th>IZ</th><th>STREBIAN</th><th>Niveau</th>
      </tr></thead>
      <tbody id="madsur-tbody"></tbody>
    </table>
  </div>
  <div id="madsur-dta" style="display:none"></div>
</div>

<div id="tab-oh" class="panel">
  <div class="sect-title"><i class="ti ti-git-merge" aria-hidden="true"></i>Convergence One Health — Signaux croisés SIMR × MADSUR</div>
  <div id="oh-cards"></div>
  <div class="sect-title" style="margin-top:20px"><i class="ti ti-layout-columns" aria-hidden="true"></i>Tableau de bord triplé — Humain | Animal | Environnement</div>
  <div class="oh-grid">
    <div class="oh-col">
      <div class="oh-col-hdr" style="background:#E53935">Humain (SIMR/DHIS2)</div>
      <div class="oh-col-body" id="oh-h"></div>
    </div>
    <div class="oh-col">
      <div class="oh-col-hdr" style="background:#FB8C00">Animal (MADSUR)</div>
      <div class="oh-col-body" id="oh-a"></div>
    </div>
    <div class="oh-col">
      <div class="oh-col-hdr" style="background:#006064">Environnement (MEEF)</div>
      <div class="oh-col-body" id="oh-e"></div>
    </div>
  </div>
</div>

<div id="tab-top5-oh" class="panel">
  <div class="sect-title"><i class="ti ti-podium" style="color:#C9A84C" aria-hidden="true"></i>Top 5 maladies prioritaires SIMR — SE 22</div>
  <div id="top5-oh-cards" style="display:flex;flex-direction:column;gap:10px;margin-bottom:16px;"></div>
  <div class="card">
    <div class="ct"><div class="ct-l"><i class="ti ti-chart-radar" style="color:#4A148C" aria-hidden="true"></i>Matrice de risque — Probabilité × Impact</div></div>
    <div style="position:relative;height:240px;"><canvas id="risk-matrix-oh"></canvas></div>
    <div style="display:flex;flex-wrap:wrap;gap:10px;margin-top:8px;font-size:11px;color:var(--color-text-secondary);" id="risk-legend-oh"></div>
  </div>
</div>

<div id="tab-croisee-oh" class="panel">
  <div class="sect-title"><i class="ti ti-arrows-cross" style="color:#0F1F5C" aria-hidden="true"></i>Analyse croisée One Health — Signaux convergents SE 22</div>
  <div id="cross-signals-oh" style="display:flex;flex-direction:column;gap:8px;margin-bottom:16px;"></div>
  <div style="display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:12px;">
    <div class="card">
      <div class="ct"><div class="ct-l"><i class="ti ti-chart-dots" style="color:#006064" aria-hidden="true"></i>Convergence spatiale humain–animal</div></div>
      <div style="position:relative;height:190px;"><canvas id="convergence-chart-oh"></canvas></div>
    </div>
    <div class="card">
      <div class="ct"><div class="ct-l"><i class="ti ti-timeline" style="color:#4A148C" aria-hidden="true"></i>Fenêtre temporelle — signaux croisés SE18–22</div></div>
      <div style="position:relative;height:190px;"><canvas id="timeline-chart-oh"></canvas></div>
    </div>
  </div>
  <div class="card">
    <div class="ct"><div class="ct-l"><i class="ti ti-dna" style="color:#B71C1C" aria-hidden="true"></i>Agents pathogènes zoonoses — Statut investigation</div>
      <button class="btn-p" onclick="sendPrompt('Rédige la section 7 Analyse One Health du Bulletin SE22')">Section 7 bulletin ↗</button>
    </div>
    <div style="overflow-x:auto;">
      <table style="width:100%;border-collapse:collapse;font-size:11px;" id="zoonose-table-oh">
        <thead><tr style="border-bottom:.5px solid var(--color-border-tertiary);">
          <th style="text-align:left;padding:5px 8px;font-weight:500;color:var(--color-text-secondary);">Agent</th>
          <th style="text-align:left;padding:5px 8px;font-weight:500;color:var(--color-text-secondary);">Signal humain</th>
          <th style="text-align:left;padding:5px 8px;font-weight:500;color:var(--color-text-secondary);">Signal animal</th>
          <th style="text-align:left;padding:5px 8px;font-weight:500;color:var(--color-text-secondary);">Zone convergence</th>
          <th style="text-align:center;padding:5px 8px;font-weight:500;color:var(--color-text-secondary);">STREBIAN</th>
          <th style="text-align:center;padding:5px 8px;font-weight:500;color:var(--color-text-secondary);">Priorité</th>
        </tr></thead>
        <tbody id="zoonose-tbody-oh"></tbody>
      </table>
    </div>
  </div>
</div>

<div id="tab-bulletin" class="panel">

<style>
/* ── BULLETIN ÉPIDÉMIOLOGIQUE ── */
.bull-wrap{max-width:900px;margin:0 auto;padding:0 4px;}
.bull-header{background:linear-gradient(135deg,#0F1F5C 0%,#1a3480 100%);color:#fff;border-radius:10px;padding:18px 20px;margin-bottom:14px;}
.bull-header-top{display:flex;align-items:flex-start;justify-content:space-between;gap:12px;flex-wrap:wrap;}
.bull-logo-zone{display:flex;align-items:center;gap:10px;}
.bull-logo-badge{background:#C9A84C;color:#0F1F5C;font-size:11px;font-weight:700;padding:4px 10px;border-radius:5px;letter-spacing:.5px;}
.bull-title{font-size:15px;font-weight:700;margin-top:4px;letter-spacing:.2px;}
.bull-subtitle{font-size:11px;opacity:.7;margin-top:2px;}
.bull-meta{text-align:right;font-size:10px;opacity:.65;line-height:1.7;}
.bull-divider{border:none;border-top:.5px solid rgba(255,255,255,0.2);margin:12px 0;}
.bull-resexec{background:rgba(255,255,255,0.08);border-radius:7px;padding:12px 14px;font-size:12px;line-height:1.7;}
.bull-resexec strong{color:#C9A84C;}
.bull-section-title{font-size:11px;font-weight:600;color:var(--color-text-secondary);letter-spacing:.8px;text-transform:uppercase;margin:14px 0 8px;padding-bottom:4px;border-bottom:.5px solid var(--color-border-tertiary);}
.bull-grid2{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:12px;}
.bull-grid3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:10px;margin-bottom:12px;}
.bull-kpi-row{display:grid;grid-template-columns:repeat(auto-fit,minmax(100px,1fr));gap:8px;margin-bottom:14px;}
.bull-kpi{background:#fff;border:.5px solid var(--color-border-tertiary);border-radius:8px;padding:10px 12px;text-align:center;}
.bull-kpi-v{font-size:22px;font-weight:700;line-height:1.1;}
.bull-kpi-l{font-size:9px;color:var(--color-text-secondary);margin-top:3px;line-height:1.3;}
.bull-kpi-s{font-size:9px;margin-top:2px;}
.bull-card{background:#fff;border:.5px solid var(--color-border-tertiary);border-radius:8px;padding:12px 14px;margin-bottom:10px;}
.bull-card-title{font-size:12px;font-weight:500;margin-bottom:8px;display:flex;align-items:center;gap:6px;}
.bull-signal-row{display:flex;flex-direction:column;gap:6px;}
.bull-signal{border-radius:6px;padding:9px 11px;border-left:4px solid;}
.bull-signal-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:4px;}
.bull-signal-id{font-size:10px;font-weight:600;opacity:.8;}
.bull-signal-mal{font-size:12px;font-weight:500;}
.bull-signal-reg{font-size:10px;opacity:.8;}
.bull-signal-body{font-size:11px;line-height:1.5;color:var(--color-text-secondary);}
.bull-signal-meta{display:flex;gap:6px;flex-wrap:wrap;margin-top:5px;}
.bull-pill-sm{font-size:9px;padding:1px 7px;border-radius:3px;font-weight:500;}
.bull-717{background:var(--color-background-secondary);border-radius:7px;padding:10px 12px;}
.bull-717-row{display:flex;align-items:center;gap:8px;margin-bottom:4px;font-size:11px;}
.bull-717-bar{flex:1;background:var(--color-background-tertiary);height:6px;border-radius:3px;overflow:hidden;}
.bull-717-fill{height:100%;border-radius:3px;}
.bull-717-label{min-width:80px;font-weight:500;}
.bull-717-val{min-width:40px;text-align:right;font-weight:600;}
.bull-streb-table{width:100%;border-collapse:collapse;font-size:11px;}
.bull-streb-table th{text-align:left;padding:5px 8px;font-weight:500;color:var(--color-text-secondary);border-bottom:.5px solid var(--color-border-tertiary);}
.bull-streb-table td{padding:5px 8px;border-bottom:.5px solid var(--color-border-tertiary);}
.bull-streb-table tr:nth-child(even){background:var(--color-background-secondary);}
.bull-reco-row{display:flex;flex-direction:column;gap:6px;}
.bull-reco{border-radius:6px;padding:9px 11px;}
.bull-reco-title{font-size:11px;font-weight:600;margin-bottom:5px;display:flex;align-items:center;gap:5px;}
.bull-reco-item{display:flex;align-items:flex-start;gap:5px;font-size:11px;margin-bottom:3px;}
.bull-actions{display:flex;gap:8px;flex-wrap:wrap;margin-top:14px;padding-top:12px;border-top:.5px solid var(--color-border-tertiary);}
.bull-btn{background:#0F1F5C;color:#fff;border:none;border-radius:5px;padding:7px 13px;font-size:11px;cursor:pointer;display:flex;align-items:center;gap:5px;font-family:var(--font-sans);}
.bull-btn:hover{background:#1a3480;}
.bull-btn-sec{background:#fff;border:.5px solid var(--color-border-secondary);color:var(--color-text-primary);border-radius:5px;padding:7px 13px;font-size:11px;cursor:pointer;display:flex;align-items:center;gap:5px;font-family:var(--font-sans);}
.bull-btn-sec:hover{background:var(--color-background-secondary);}
.bull-oh-grid{display:grid;grid-template-columns:1fr 1fr 1fr;gap:8px;}
.bull-oh-col{border-radius:7px;overflow:hidden;}
.bull-oh-col-hdr{font-size:11px;font-weight:600;color:#fff;padding:7px 10px;}
.bull-oh-item{font-size:10px;padding:5px 9px;border-bottom:.5px solid rgba(0,0,0,0.06);line-height:1.4;}
.bull-oh-item:nth-child(odd){background:rgba(255,255,255,0.5);}
@media(max-width:600px){.bull-grid2,.bull-grid3,.bull-oh-grid{grid-template-columns:1fr;}.bull-kpi-row{grid-template-columns:repeat(2,1fr);}}
</style>

<div class="bull-wrap">

  <!-- ─── EN-TÊTE BULLETIN ─── -->
  <div class="bull-header">
    <div class="bull-header-top">
      <div class="bull-logo-zone">
        <div>
          <div style="display:flex;gap:8px;align-items:center;margin-bottom:4px;">
            <span class="bull-logo-badge">ONE HEALTH</span>
            <span style="font-size:10px;opacity:.7;">SBESOH · FHI360/STRIDES Madagascar</span>
          </div>
          <div class="bull-title">BULLETIN ÉPIDÉMIOLOGIQUE ONE HEALTH</div>
          <div class="bull-subtitle">Semaine Épidémiologique 22 · 26 mai – 1 juin 2026 · Madagascar</div>
        </div>
      </div>
      <div class="bull-meta">
        <div><strong>N°</strong> SE22/2026</div>
        <div><strong>Émis par :</strong> DVSSER + DSV/MAEP</div>
        <div><strong>Appui technique :</strong> FHI360 STRIDES</div>
        <div><strong>Date :</strong> 28 mai 2026</div>
        <div><strong>Distribution :</strong> Restricted — MSANP, CDC, OMS</div>
      </div>
    </div>
    <hr class="bull-divider">
    <div class="bull-resexec">
      <strong>Résumé exécutif SE 22 :</strong> Semaine marquée par 3 signaux ROUGE actifs et 4 ORANGE. Signal zoonose confirmé : foyer rage Anjozorobe (MAD-01 bovin + SIM-01 humain, 1 décès). MPox en progression nationale (7 cas, 5 régions, +75% vs SE21). Influenza aviaire H5N1 Boeny confirmé (STR-0441). Anthrax suspect Melaky en attente STR-0450 urgent. Indicateurs 7-1-7 conformes : détection 4.8j ✓, notification 1.2j ✓, riposte 5.1j ✓. Complétude nationale 76% — 6 districts non déclarants. 
      <br><strong style="color:#FF8F00;">Action prioritaire :</strong> Mobilisation immédiate équipe OH Anjozorobe · Réponse STR-0450 Melaky · Notification IHR rage + MPox en cours.
    </div>
  </div>

  <!-- ─── KPIs GLOBAUX ─── -->
  <div class="bull-section-title"><i class="ti ti-chart-bar" style="margin-right:4px"></i>Indicateurs clés — SE 22</div>
  <div class="bull-kpi-row">
    <div class="bull-kpi"><div class="bull-kpi-v">1 247</div><div class="bull-kpi-l">Total cas SIMR SE22</div><div class="bull-kpi-s" style="color:#E65100;">↑ +8% vs SE21</div></div>
    <div class="bull-kpi"><div class="bull-kpi-v" style="color:#B71C1C;">3</div><div class="bull-kpi-l">Signaux ROUGE actifs</div><div class="bull-kpi-s" style="color:#B71C1C;">Rage · MPox · IA H5N1</div></div>
    <div class="bull-kpi"><div class="bull-kpi-v" style="color:#E65100;">4</div><div class="bull-kpi-l">Signaux ORANGE</div><div class="bull-kpi-s">Paludisme · Choléra · Anthrax · FMD</div></div>
    <div class="bull-kpi"><div class="bull-kpi-v">23</div><div class="bull-kpi-l">Signaux MADSUR SE22</div><div class="bull-kpi-s" style="color:#006064;">10 maladies animales</div></div>
    <div class="bull-kpi"><div class="bull-kpi-v">14</div><div class="bull-kpi-l">Décès notifiés</div><div class="bull-kpi-s">CFR global 1.1%</div></div>
    <div class="bull-kpi"><div class="bull-kpi-v">76%</div><div class="bull-kpi-l">Complétude rapportage</div><div class="bull-kpi-s" style="color:#F57F17;">6 districts non déclarants</div></div>
    <div class="bull-kpi"><div class="bull-kpi-v">4.8j</div><div class="bull-kpi-l">Délai détection moyen</div><div class="bull-kpi-s" style="color:#1B5E20;">✓ Cible ≤7j</div></div>
    <div class="bull-kpi"><div class="bull-kpi-v">4</div><div class="bull-kpi-l">STREBIAN actifs SE22</div><div class="bull-kpi-s" style="color:#B71C1C;">2 POSITIFS</div></div>
  </div>

  <div class="bull-grid2">

    <!-- ─── COL GAUCHE ─── -->
    <div>

      <div class="bull-section-title"><i class="ti ti-alert-triangle" style="margin-right:4px"></i>Signaux prioritaires — ROUGE & ORANGE</div>

      <div class="bull-signal-row">

        <div class="bull-signal" style="background:#FCEBEB;border-color:#B71C1C;">
          <div class="bull-signal-header">
            <span class="bull-signal-id">SIM-01 + MAD-01</span>
            <div style="display:flex;gap:4px;"><span class="bull-pill-sm" style="background:#B71C1C;color:#fff;">ROUGE</span><span class="bull-pill-sm" style="background:#FFCDD2;color:#B71C1C;">ZOONOSE</span></div>
          </div>
          <div class="bull-signal-mal">Rage humaine + bovine — Analamanga (Anjozorobe)</div>
          <div class="bull-signal-body">1 décès humain (morsure chien), 3 cas PEP actifs. 12 bovins morts (STR-0442 POSITIF). Transmission chien→bovin→humain documentée. Équipe OH mobilisée.</div>
          <div class="bull-signal-meta">
            <span class="bull-pill-sm" style="background:#FFE0B2;color:#E65100;">IZ=0.85</span>
            <span class="bull-pill-sm" style="background:#E6F1FB;color:#0F1F5C;">Riposte J3/7-1-7</span>
            <span class="bull-pill-sm" style="background:#E8F5E9;color:#1B5E20;">PEP initié</span>
          </div>
        </div>

        <div class="bull-signal" style="background:#FCEBEB;border-color:#B71C1C;">
          <div class="bull-signal-header">
            <span class="bull-signal-id">SIM-02</span>
            <div style="display:flex;gap:4px;"><span class="bull-pill-sm" style="background:#B71C1C;color:#fff;">ROUGE</span><span class="bull-pill-sm" style="background:#FFCDD2;color:#B71C1C;">VEILLE IHR</span></div>
          </div>
          <div class="bull-signal-mal">MPox — Progression nationale · 5 régions</div>
          <div class="bull-signal-body">7 cas confirmés PCR (Clade II) SE22 vs 4 SE21 (+75%). Régions : Analamanga (3), Boeny (2), Diana (1), Atsinanana (1). Génotypage CNRE en cours. Réservoir animal non identifié.</div>
          <div class="bull-signal-meta">
            <span class="bull-pill-sm" style="background:#FFE0B2;color:#E65100;">+75% SE21</span>
            <span class="bull-pill-sm" style="background:#E6F1FB;color:#0F1F5C;">Notification Africa CDC</span>
            <span class="bull-pill-sm" style="background:#FFFDE7;color:#F57F17;">Génotypage en cours</span>
          </div>
        </div>

        <div class="bull-signal" style="background:#FFECB3;border-color:#E65100;">
          <div class="bull-signal-header">
            <span class="bull-signal-id">MAD-03</span>
            <div style="display:flex;gap:4px;"><span class="bull-pill-sm" style="background:#E65100;color:#fff;">ORANGE</span><span class="bull-pill-sm" style="background:#FFE0B2;color:#E65100;">ZOONOSE</span></div>
          </div>
          <div class="bull-signal-mal">Influenza aviaire H5N1 — Boeny (volailles)</div>
          <div class="bull-signal-body">340 volailles touchées, 280 décès (létalité 82%). STR-0441 POSITIF H5N1 confirmé. Abattage préventif en cours. Surveillance humaine active dans rayon 20km. Aucun cas humain à ce jour.</div>
          <div class="bull-signal-meta">
            <span class="bull-pill-sm" style="background:#FFCDD2;color:#B71C1C;">STR-0441 POSITIF</span>
            <span class="bull-pill-sm" style="background:#E6F1FB;color:#0F1F5C;">Notif. OIE+FAO</span>
            <span class="bull-pill-sm" style="background:#E8F5E9;color:#1B5E20;">Humain : 0 cas</span>
          </div>
        </div>

        <div class="bull-signal" style="background:#FFF3E0;border-color:#E65100;">
          <div class="bull-signal-header">
            <span class="bull-signal-id">MAD-05</span>
            <div style="display:flex;gap:4px;"><span class="bull-pill-sm" style="background:#E65100;color:#fff;">ORANGE</span><span class="bull-pill-sm" style="background:#FFE0B2;color:#E65100;">URGENT</span></div>
          </div>
          <div class="bull-signal-mal">Anthrax suspect — Melaky (3 zébus morts)</div>
          <div class="bull-signal-body">3 zébus retrouvés morts (létalité 100%). IZ=0.65. Exposition humaine éleveurs possible. STR-0450 résultat attendu en urgence. Zone cordon sanitaire 2km activée.</div>
          <div class="bull-signal-meta">
            <span class="bull-pill-sm" style="background:#FFCDD2;color:#B71C1C;">STR-0450 URGENT</span>
            <span class="bull-pill-sm" style="background:#FFE0B2;color:#E65100;">Exposition humaine possible</span>
          </div>
        </div>

        <div class="bull-signal" style="background:#FFF8E1;border-color:#F57F17;">
          <div class="bull-signal-header">
            <span class="bull-signal-id">SIM-03</span>
            <div style="display:flex;gap:4px;"><span class="bull-pill-sm" style="background:#F57F17;color:#fff;">ORANGE</span></div>
          </div>
          <div class="bull-signal-mal">Paludisme grave — SAVA (Sambava)</div>
          <div class="bull-signal-body">18 cas, 2 décès (&lt;5 ans). Dépasse seuil épidémique. Rupture partielle ACT Sambava (30%). Pic saisonnier — renforcement prise en charge urgent.</div>
          <div class="bull-signal-meta">
            <span class="bull-pill-sm" style="background:#FFCDD2;color:#B71C1C;">2 décès &lt;5 ans</span>
            <span class="bull-pill-sm" style="background:#FFE0B2;color:#E65100;">Rupture ACT 30%</span>
          </div>
        </div>

      </div>

    </div>

    <!-- ─── COL DROITE ─── -->
    <div>

      <div class="bull-section-title"><i class="ti ti-flask" style="margin-right:4px"></i>Résultats STREBIAN — SE 22</div>
      <div class="bull-card">
        <table class="bull-streb-table">
          <thead><tr>
            <th>Réf.</th><th>Échantillon</th><th>Région</th><th>Résultat</th><th>Action</th>
          </tr></thead>
          <tbody>
            <tr><td><strong>STR-0441</strong></td><td>Volailles mortes</td><td>Boeny</td><td><span class="bull-pill-sm" style="background:#B71C1C;color:#fff;">POSITIF H5N1</span></td><td style="font-size:10px;color:#B71C1C;">Abattage + notif. OIE</td></tr>
            <tr><td><strong>STR-0442</strong></td><td>Tissu bovin / salive chien</td><td>Analamanga</td><td><span class="bull-pill-sm" style="background:#B71C1C;color:#fff;">POSITIF Rage</span></td><td style="font-size:10px;color:#B71C1C;">Riposte OH active</td></tr>
            <tr><td><strong>STR-0443</strong></td><td>Écouvillons cloaque volaille</td><td>Boeny</td><td><span class="bull-pill-sm" style="background:#FFF9C4;color:#F57F17;">EN COURS</span></td><td style="font-size:10px;color:#F57F17;">Résultat J+2</td></tr>
            <tr><td><strong>STR-0445</strong></td><td>Sérum bovin / eau</td><td>Boeny</td><td><span class="bull-pill-sm" style="background:#FFF9C4;color:#F57F17;">EN COURS</span></td><td style="font-size:10px;color:#F57F17;">Lepto. suspecte</td></tr>
            <tr><td><strong>STR-0446</strong></td><td>Sérum bovin</td><td>Vakinankaratra</td><td><span class="bull-pill-sm" style="background:#FFF9C4;color:#F57F17;">EN COURS</span></td><td style="font-size:10px;color:#F57F17;">Brucella suspect</td></tr>
            <tr><td><strong>STR-0448</strong></td><td>Épithélium vésicule</td><td>Vakinankaratra</td><td><span class="bull-pill-sm" style="background:#FFF9C4;color:#F57F17;">EN COURS</span></td><td style="font-size:10px;color:#F57F17;">FMD typisation</td></tr>
            <tr><td><strong>STR-0449</strong></td><td>Prélèv. nasal humain</td><td>Toamasina</td><td><span class="bull-pill-sm" style="background:#FFF9C4;color:#F57F17;">EN COURS</span></td><td style="font-size:10px;color:#F57F17;">Choléra PCR</td></tr>
            <tr><td><strong style="color:#B71C1C;">STR-0450</strong></td><td>Sol / rate zébu</td><td>Melaky</td><td><span class="bull-pill-sm" style="background:#FFCDD2;color:#B71C1C;">URGENT</span></td><td style="font-size:10px;color:#B71C1C;">Anthrax — 24h max</td></tr>
          </tbody>
        </table>
      </div>

      <div class="bull-section-title"><i class="ti ti-clock" style="margin-right:4px"></i>Indicateurs 7-1-7 — SE 22</div>
      <div class="bull-card">
        <div class="bull-717">
          <div style="font-size:11px;font-weight:500;color:var(--color-text-primary);margin-bottom:8px;">Délais de riposte — Cadre OMS 7-1-7</div>
          <div class="bull-717-row">
            <span class="bull-717-label" style="color:#0F1F5C;">Détection</span>
            <div class="bull-717-bar"><div class="bull-717-fill" style="width:69%;background:#1B5E20;"></div></div>
            <span class="bull-717-val" style="color:#1B5E20;">4.8j ✓</span>
            <span style="font-size:9px;color:var(--color-text-secondary);">/ 7j</span>
          </div>
          <div class="bull-717-row">
            <span class="bull-717-label" style="color:#0F1F5C;">Notification</span>
            <div class="bull-717-bar"><div class="bull-717-fill" style="width:100%;background:#1B5E20;"></div></div>
            <span class="bull-717-val" style="color:#1B5E20;">1.2j ✓</span>
            <span style="font-size:9px;color:var(--color-text-secondary);">/ 1j</span>
          </div>
          <div class="bull-717-row">
            <span class="bull-717-label" style="color:#0F1F5C;">Riposte</span>
            <div class="bull-717-bar"><div class="bull-717-fill" style="width:73%;background:#1B5E20;"></div></div>
            <span class="bull-717-val" style="color:#1B5E20;">5.1j ✓</span>
            <span style="font-size:9px;color:var(--color-text-secondary);">/ 7j</span>
          </div>
          <div class="bull-717-row">
            <span class="bull-717-label" style="color:#F57F17;">Complétude</span>
            <div class="bull-717-bar"><div class="bull-717-fill" style="width:76%;background:#F57F17;"></div></div>
            <span class="bull-717-val" style="color:#F57F17;">76% ⚠</span>
            <span style="font-size:9px;color:var(--color-text-secondary);">/ 100%</span>
          </div>
        </div>
        <div style="margin-top:8px;font-size:10px;color:var(--color-text-secondary);background:var(--color-background-secondary);border-radius:5px;padding:7px 9px;">
          <strong style="color:#F57F17;">⚠ 6 districts non déclarants SE22 :</strong> Ambatosoa, Tsaratanana, Befotaka, Vohipeno, Betroka, Marolambo — Rappel E1 envoyé le 27/05/2026.
        </div>
      </div>

      <div class="bull-section-title"><i class="ti ti-git-merge" style="margin-right:4px"></i>Convergence One Health</div>
      <div class="bull-card">
        <div class="bull-oh-grid">
          <div class="bull-oh-col">
            <div class="bull-oh-col-hdr" style="background:#E53935;"><i class="ti ti-user-heart"></i> Humain (SIMR)</div>
            <div class="bull-oh-item">Rage · Anjozorobe (1 décès)</div>
            <div class="bull-oh-item">MPox · 5 régions · +75%</div>
            <div class="bull-oh-item">Paludisme grave · SAVA</div>
            <div class="bull-oh-item">Leptospirose · Boeny (4 cas)</div>
            <div class="bull-oh-item">IRA sévère cluster · HM</div>
          </div>
          <div class="bull-oh-col">
            <div class="bull-oh-col-hdr" style="background:#FB8C00;"><i class="ti ti-pig"></i> Animal (MADSUR)</div>
            <div class="bull-oh-item">Rage bovine · Analamanga (IZ=0.85)</div>
            <div class="bull-oh-item">H5N1 volailles · Boeny (IZ=0.55)</div>
            <div class="bull-oh-item">Anthrax zébus · Melaky (IZ=0.65)</div>
            <div class="bull-oh-item">Leptospirose bovine · Boeny</div>
            <div class="bull-oh-item">FMD · Vakinankaratra (45 cas)</div>
          </div>
          <div class="bull-oh-col">
            <div class="bull-oh-col-hdr" style="background:#006064;"><i class="ti ti-leaf"></i> Environnement</div>
            <div class="bull-oh-item">Inondations côtières · Toamasina</div>
            <div class="bull-oh-item">Saison pluies · SAVA · vecteurs</div>
            <div class="bull-oh-item">Déforestation · Melaky · anthrax</div>
            <div class="bull-oh-item">Marchés volailles · Boeny · H5</div>
            <div class="bull-oh-item">Chiens errants · Anjozorobe · rage</div>
          </div>
        </div>
      </div>

      <div class="bull-section-title"><i class="ti ti-list-check" style="margin-right:4px"></i>Recommandations actionnables</div>
      <div class="bull-reco-row">
        <div class="bull-reco" style="background:#FFEBEE;border:.5px solid #EF9F9F;">
          <div class="bull-reco-title" style="color:#B71C1C;"><i class="ti ti-clock" style="font-size:14px"></i>IMMÉDIAT — Dans les 24h</div>
          <div class="bull-reco-item"><i class="ti ti-arrow-right" style="color:#B71C1C;font-size:12px;margin-top:1px;flex-shrink:0;"></i><span>Déployer équipe OH Anjozorobe (DSV+MSANP+GIV) — rage confirmée humain+animal</span></div>
          <div class="bull-reco-item"><i class="ti ti-arrow-right" style="color:#B71C1C;font-size:12px;margin-top:1px;flex-shrink:0;"></i><span>Résultat STR-0450 Melaky en priorité absolue — anthrax suspect avec exposition humaine</span></div>
          <div class="bull-reco-item"><i class="ti ti-arrow-right" style="color:#B71C1C;font-size:12px;margin-top:1px;flex-shrink:0;"></i><span>Traçage exhaustif contacts MPox DIANA+Analamanga (8 contacts en quarantaine)</span></div>
        </div>
        <div class="bull-reco" style="background:#FFF3E0;border:.5px solid #FBBF85;">
          <div class="bull-reco-title" style="color:#E65100;"><i class="ti ti-clock-hour-3" style="font-size:14px"></i>URGENT — 48–72h</div>
          <div class="bull-reco-item"><i class="ti ti-arrow-right" style="color:#E65100;font-size:12px;margin-top:1px;flex-shrink:0;"></i><span>Réappro urgente ACT Sambava (SALAMA) — rupture 30%, 2 décès &lt;5 ans</span></div>
          <div class="bull-reco-item"><i class="ti ti-arrow-right" style="color:#E65100;font-size:12px;margin-top:1px;flex-shrink:0;"></i><span>Notification OIE/FAO H5N1 Boeny + séquençage génomique souche aviaire</span></div>
          <div class="bull-reco-item"><i class="ti ti-arrow-right" style="color:#E65100;font-size:12px;margin-top:1px;flex-shrink:0;"></i><span>Investigation environnementale MEEF — source eau bovins+humains Boeny (leptospirose)</span></div>
        </div>
        <div class="bull-reco" style="background:#FFFDE7;border:.5px solid #F9E06E;">
          <div class="bull-reco-title" style="color:#F57F17;"><i class="ti ti-clock-hour-6" style="font-size:14px"></i>7 JOURS — Action planifiée</div>
          <div class="bull-reco-item"><i class="ti ti-arrow-right" style="color:#F57F17;font-size:12px;margin-top:1px;flex-shrink:0;"></i><span>Campagne VAR canine + bovine Anjozorobe (5km périmètre) — prévention rage secondaire</span></div>
          <div class="bull-reco-item"><i class="ti ti-arrow-right" style="color:#F57F17;font-size:12px;margin-top:1px;flex-shrink:0;"></i><span>Distribution MILD 2 fokontany prioritaires SAVA + pulvérisation intra-domiciliaire</span></div>
          <div class="bull-reco-item"><i class="ti ti-arrow-right" style="color:#F57F17;font-size:12px;margin-top:1px;flex-shrink:0;"></i><span>6 districts non déclarants : transmission rapport SIMR SE22 avant 31/05/2026</span></div>
        </div>
      </div>

      <div class="bull-section-title"><i class="ti ti-chart-line" style="margin-right:4px"></i>Tendances SE 18–22</div>
      <div class="bull-card" style="padding:10px;">
        <div style="position:relative;height:180px;"><canvas id="bull-trend-chart" role="img" aria-label="Tendances signaux SIMR+MADSUR SE18-SE22">SIMR total et signaux MADSUR par semaine épidémiologique</canvas></div>
        <script>
        (function(){
          const ctx = document.getElementById('bull-trend-chart');
          if(ctx && typeof Chart !== 'undefined') {
            new Chart(ctx, {
              type:'line',
              data:{
                labels:['SE18','SE19','SE20','SE21','SE22'],
                datasets:[
                  {label:'Cas SIMR /10',data:[98,105,134,115,125],borderColor:'#0F1F5C',backgroundColor:'rgba(15,31,92,0.07)',fill:true,tension:0.3,pointRadius:4,borderWidth:2},
                  {label:'Signaux MADSUR',data:[12,14,18,20,23],borderColor:'#006064',backgroundColor:'rgba(0,96,100,0.07)',fill:true,tension:0.3,pointRadius:4,borderWidth:2,borderDash:[4,2]},
                  {label:'MPox',data:[3,2,4,4,7],borderColor:'#B71C1C',backgroundColor:'rgba(183,28,28,0.07)',fill:false,tension:0.3,pointRadius:4,borderWidth:2},
                ]
              },
              options:{
                responsive:true,maintainAspectRatio:false,
                plugins:{legend:{display:true,labels:{font:{size:10},boxWidth:12}}},
                scales:{x:{ticks:{font:{size:10},autoSkip:false}},y:{ticks:{font:{size:10}},beginAtZero:true}}
              }
            });
          }
        })();
        </script>
      </div>

    </div>
  </div>

  <!-- ─── PIED DE BULLETIN ─── -->
  <div style="background:var(--color-background-secondary);border:.5px solid var(--color-border-tertiary);border-radius:8px;padding:10px 14px;margin-top:14px;font-size:10px;color:var(--color-text-secondary);line-height:1.7;">
    <strong style="color:var(--color-text-primary);">Prochaine émission :</strong> SE 23 — 04 juin 2026 · 
    <strong>Contact :</strong> DVSSER/MSANP · dvsser@sante.gov.mg · 
    <strong>Appui technique :</strong> FHI360 STRIDES Madagascar · 
    <strong>Distribution :</strong> MSANP, CDC Madagascar, OMS Madagascar, DSV/MAEP, Africa CDC, GHSA Partners · 
    <em>Ce bulletin est produit dans le cadre du projet STRIDES financé par USAID/CDC. Reproduction autorisée avec mention de la source.</em>
  </div>

  <!-- ─── ACTIONS IA ─── -->
  <div class="bull-actions">
    <button class="bull-btn" onclick="sendPrompt('Rédige le bulletin épidémiologique complet SE22 One Health Madagascar : rage Anjozorobe (zoonose confirmée), MPox progression 5 régions, H5N1 Boeny, anthrax Melaky, paludisme SAVA. Format DVSSER officiel.')"><i class="ti ti-sparkles"></i>Rédiger bulletin complet ↗</button>
    <button class="bull-btn" onclick="sendPrompt('Rédige les recommandations actionnables du bulletin SE22 par niveau : national DVSSER+DSV, régional DRS+DREEF, district EMAD+MI+SV')"><i class="ti ti-list-check"></i>Recommandations par niveau ↗</button>
    <button class="bull-btn-sec" onclick="sendPrompt('Génère le message SMS/WhatsApp d alert pour les 7 districts en riposte SE22 : Anjozorobe, Antsiranana, Sambava, Mahajanga, Melaky, Toamasina, Fianarantsoa')"><i class="ti ti-brand-whatsapp"></i>SMS/WhatsApp alerte ↗</button>
    <button class="bull-btn-sec" onclick="sendPrompt('Analyse comparative SE22 vs SE18-21 : quelles tendances préoccupantes ? Rage, MPox, paludisme — projections SE23')"><i class="ti ti-chart-line"></i>Tendances SE18–22 ↗</button>
    <button class="bull-btn-sec" onclick="sendPrompt('Rédige le communiqué de presse MSANP pour le foyer rage Anjozorobe et le cas MPox DIANA SE22')"><i class="ti ti-news"></i>Communiqué de presse ↗</button>
  </div>

</div>

</div>

</div>

<script>
const SIMR = [
  {id:'SIM-01',mal:'Rage humaine',reg:'Analamanga',dist:'Antananarivo-Renivohitra',cas:3,deces:1,letal:'33%',trend:'↑↑',alerte:'ROUGE',det:3,notif:1,rip:5,sa:0.80,sh:0.90,cs:0.60,str:0.85,
   kpis:{cas:'3',deces:'1',letal:'33%',score:'0.82'},
   desc:'Rage humaine confirmée en lien avec le foyer bovin MAD-01. 1 décès enregistré, 3 cas suspects sous traitement PEP. Transmission par morsure de chien errant.',
   actions:[
     {cls:'act-imm',tag:'IMMÉDIAT',txt:'Activer protocole PEP pour tout contact exposé — délai max 24h'},
     {cls:'act-imm',tag:'IMMÉDIAT',txt:'Notifier MSANP/DVSSER + CDC Madagascar dans les 12h'},
     {cls:'act-urg',tag:'URGENT 48h',txt:'Recensement chiens errants Antananarivo-Renivohitra + vaccination de masse'},
     {cls:'act-7j',tag:'7 JOURS',txt:'Campagne VAR (vaccination anti-rabique) communautaire avec GIV/DSV'},
     {cls:'act-surv',tag:'SURVEILLER',txt:'Monitoring quotidien cas humains SE22-SE25 + signalement tout décès suspect'},
   ],trends:[2,1,0,1,3]},
  {id:'SIM-02',mal:'MPox',reg:'DIANA',dist:'Antsiranana I',cas:2,deces:0,letal:'0%',trend:'↑',alerte:'ROUGE',det:5,notif:1,rip:3,sa:0.50,sh:0.80,cs:0.50,str:0.60,
   kpis:{cas:'2',deces:'0',letal:'0%',score:'0.61'},
   desc:'2 cas MPox confirmés PCR, Clade II. Contacts tracés : 8 personnes en quarantaine. Aucun lien avec réservoir animal identifié pour l\'instant.',
   actions:[
     {cls:'act-imm',tag:'IMMÉDIAT',txt:'Isolement strict des 2 cas confirmés + traçage exhaustif contacts'},
     {cls:'act-urg',tag:'URGENT 48h',txt:'Déploiement EMAR DIANA + notification MSANP/OMS'},
     {cls:'act-7j',tag:'7 JOURS',txt:'Investigation source (voyage récent, contact animal) + séquençage phylogénétique'},
     {cls:'act-30j',tag:'30 JOURS',txt:'Évaluation vaccination ring si propagation confirmée'},
     {cls:'act-surv',tag:'SURVEILLER',txt:'Surveillance active milieu hospitalier DIANA + points d\'entrée portuaires'},
   ],trends:[0,0,0,1,2]},
  {id:'SIM-03',mal:'Paludisme grave',reg:'SAVA',dist:'Sambava',cas:18,deces:2,letal:'11%',trend:'↑',alerte:'ORANGE',det:4,notif:1,rip:6,sa:0.30,sh:0.70,cs:0.40,str:0.20,
   kpis:{cas:'18',deces:'2',letal:'11%',score:'0.44'},
   desc:'Pic saisonnier paludisme grave, dépasse seuil épidémique. 2 décès enfants <5ans. Stock ACT insuffisant au CSB Sambava (rupture partielle 30%).',
   actions:[
     {cls:'act-imm',tag:'IMMÉDIAT',txt:'Réappro urgente ACT Sambava — contacter SALAMA + STRIDES supply chain'},
     {cls:'act-urg',tag:'URGENT 48h',txt:'Renforcement prise en charge CSB : formation agents sur paludisme grave'},
     {cls:'act-7j',tag:'7 JOURS',txt:'Distribution MILD 2 fokontany prioritaires + pulvérisation intra-domiciliaire'},
     {cls:'act-surv',tag:'SURVEILLER',txt:'TDR hebdomadaire SE22-SE26 + rapport mortalité <5ans'},
   ],trends:[8,10,12,14,18]},
  {id:'SIM-04',mal:'Choléra suspect',reg:'ATSINANANA',dist:'Toamasina I',cas:5,deces:0,letal:'0%',trend:'→',alerte:'ORANGE',det:6,notif:1,rip:4,sa:0.20,sh:0.60,cs:0.70,str:0.30,
   kpis:{cas:'5',deces:'0',letal:'0%',score:'0.44'},
   desc:'5 cas de diarrhée aqueuse aiguë, suspicion choléra. Prélèvements STREBIAN envoyés. Lien possible avec inondation côtière et contamination eau.',
   actions:[
     {cls:'act-imm',tag:'IMMÉDIAT',txt:'Prélèvements eau potable + résultat STR attendu <48h'},
     {cls:'act-urg',tag:'URGENT 48h',txt:'Distribution SRO + chloration points d\'eau suspects'},
     {cls:'act-7j',tag:'7 JOURS',txt:'Investigation environnementale MEEF : qualité eau + assainissement'},
     {cls:'act-surv',tag:'SURVEILLER',txt:'Surveillance diarrhée aqueuse aiguë en attente confirmation labo'},
   ],trends:[0,2,3,4,5]},
  {id:'SIM-05',mal:'IRA sévère (cluster)',reg:'HAUTE MATSIATRA',dist:'Fianarantsoa',cas:9,deces:1,letal:'11%',trend:'→',alerte:'JAUNE',det:7,notif:2,rip:7,sa:0.25,sh:0.55,cs:0.35,str:0.10,
   kpis:{cas:'9',deces:'1',letal:'11%',score:'0.35'},
   desc:'Cluster IRA sévère, suspicion virale. 1 décès enfant 2 ans. Pas de lien animal confirmé. Proximité avec foyer influenza aviaire Boeny (MAD-03) — à surveiller.',
   actions:[
     {cls:'act-urg',tag:'URGENT 48h',txt:'PCR grippe + séquençage 3 cas sévères — exclure H5 inter-espèces'},
     {cls:'act-7j',tag:'7 JOURS',txt:'Investigation épidémio cluster : école, marché, lien MADSUR'},
     {cls:'act-surv',tag:'SURVEILLER',txt:'Signalement tout nouveau décès respiratoire <5ans dans la région'},
   ],trends:[3,4,6,7,9]},
  {id:'SIM-06',mal:'Leptospirose',reg:'BOENY',dist:'Mahajanga',cas:4,deces:0,letal:'0%',trend:'→',alerte:'JAUNE',det:5,notif:2,rip:8,sa:0.40,sh:0.45,cs:0.60,str:0.25,
   kpis:{cas:'4',deces:'0',letal:'0%',score:'0.41'},
   desc:'4 cas leptospirose confirmés sérologie. Facteur de risque : contact eau de crue + animaux (MAD-02 bovin Boeny). Lien environnemental probable.',
   actions:[
     {cls:'act-7j',tag:'7 JOURS',txt:'Investigation commune avec DSV Boeny — identification foyer animal source'},
     {cls:'act-7j',tag:'7 JOURS',txt:'Protection EPI agents de terrain + traitement prophylactique si exposition'},
     {cls:'act-surv',tag:'SURVEILLER',txt:'Surveillance syndromique fièvre + ictère dans la région'},
   ],trends:[1,2,2,3,4]},
  {id:'SIM-07',mal:'Leishmaniose',reg:'MENABE',dist:'Morondava',cas:2,deces:0,letal:'0%',trend:'↓',alerte:'VERT',det:8,notif:2,rip:0,sa:0.20,sh:0.35,cs:0.30,str:0.15,
   kpis:{cas:'2',deces:'0',letal:'0%',score:'0.26'},
   desc:'2 cas leishmaniose cutanée, prise en charge standard. Réservoir canin probable. Tendance stable.',
   actions:[
     {cls:'act-30j',tag:'30 JOURS',txt:'Traitement antiparasitaire chiens domestiques avec DSV Menabe'},
     {cls:'act-surv',tag:'SURVEILLER',txt:'Surveillance vecteur phlébotomes — pièges SE24'},
   ],trends:[4,3,3,2,2]},
];

const MADSUR = [
  {id:'MAD-01',mal:'Rage bovine',reg:'Analamanga',esp:'Bovins',cas:12,deces:8,iz:0.85,streb:'STR-0442 POSITIF',niv:'ROUGE',sa:0.85,sh:0.90,cs:0.65,str:0.90,
   kpis:{cas:'12',deces:'8',pct:'18%',score:'0.85'},
   desc:'Foyer rage bovine confirmé, lié directement au signal SIM-01 (rage humaine Analamanga). 8 bovins morts, 4 en observation. Transmission chien-bovin-humain documentée.',
   actions:[
     {cls:'act-imm',tag:'IMMÉDIAT',txt:'Alerte croisée SIMR : SIM-01 rage humaine — riposte conjointe DSV+MSANP'},
     {cls:'act-imm',tag:'IMMÉDIAT',txt:'Abattage sanitaire animaux suspects + désinfection étable'},
     {cls:'act-urg',tag:'URGENT 48h',txt:'Vaccination GIV : 500 bovins périmètre 5km + recensement chiens errants'},
     {cls:'act-7j',tag:'7 JOURS',txt:'Campagne VAR communautaire conjointe — humain + animal (OH approach)'},
     {cls:'act-surv',tag:'SURVEILLER',txt:'Monitoring quotidien chiens + bovins SE22-25 + résultat STR-0442'},
   ],trends:[3,5,7,9,12]},
  {id:'MAD-02',mal:'Conta. eau/leptospirose',reg:'Boeny',esp:'Bovins',cas:7,deces:1,iz:0.42,streb:'STR-0445 EN COURS',niv:'JAUNE',sa:0.40,sh:0.45,cs:0.60,str:0.25,
   kpis:{cas:'7',deces:'1',pct:'9%',score:'0.42'},
   desc:'Contamination eau de crue, suspicion leptospirose bovine. Lien avec SIM-06 (leptospirose humaine Mahajanga). Résultat STREBIAN attendu.',
   actions:[
     {cls:'act-urg',tag:'URGENT 48h',txt:'Résultat STR-0445 prioritaire — coordination DHIS2/MADSUR leptospirose'},
     {cls:'act-7j',tag:'7 JOURS',txt:'Investigation environnementale MEEF : qualité eau abreuvement'},
     {cls:'act-surv',tag:'SURVEILLER',txt:'Surveillance troupeaux zones inondées Boeny + signalement cas humains associés'},
   ],trends:[2,3,4,5,7]},
  {id:'MAD-03',mal:'Influenza aviaire H5',reg:'Boeny',esp:'Volailles',cas:340,deces:280,iz:0.55,streb:'STR-0441 POSITIF H5N1',niv:'ORANGE',sa:0.55,sh:0.60,cs:0.45,str:0.65,
   kpis:{cas:'340',deces:'280',pct:'82%',score:'0.55'},
   desc:'Influenza aviaire H5N1 confirmé, souche non pandémique pour l\'instant. 340 volailles touchées, 280 décès. Signal SIM-05 (IRA sévère Fianarantsoa) à surveiller pour lien inter-espèces.',
   actions:[
     {cls:'act-imm',tag:'IMMÉDIAT',txt:'Abattage préventif élevages touchés + biosécurité renforcée'},
     {cls:'act-imm',tag:'IMMÉDIAT',txt:'Alerte OIE + FAO — notification foyer H5N1 Madagascar'},
     {cls:'act-urg',tag:'URGENT 48h',txt:'Séquençage génomique souche + évaluation risque pandémique'},
     {cls:'act-7j',tag:'7 JOURS',txt:'Surveillance active cas IRA humains dans rayon 20km du foyer'},
     {cls:'act-surv',tag:'SURVEILLER',txt:'Monitoring oiseaux sauvages migrateurs — piégeage sentinelle'},
   ],trends:[0,20,80,200,340]},
  {id:'MAD-04',mal:'FMD (FA bovine)',reg:'Vakinankaratra',esp:'Bovins',cas:45,deces:2,iz:0.38,streb:'STR-0448 EN COURS',niv:'JAUNE',sa:0.45,sh:0.15,cs:0.30,str:0.30,
   kpis:{cas:'45',deces:'2',pct:'7%',score:'0.38'},
   desc:'Fièvre aphteuse bovine, non zoonotique pour l\'humain. Impact économique important. 45 cas dans 3 élevages.',
   actions:[
     {cls:'act-urg',tag:'URGENT 48h',txt:'Quarantaine 3 élevages + restriction mouvements animaux'},
     {cls:'act-7j',tag:'7 JOURS',txt:'Vaccination urgente bovins non atteints — stock vaccin FMD DSV'},
     {cls:'act-30j',tag:'30 JOURS',txt:'Évaluation pertes économiques + appui indemnisation éleveurs'},
   ],trends:[0,5,15,30,45]},
  {id:'MAD-05',mal:'Anthrax suspect',reg:'Melaky',esp:'Bovins/Zébus',cas:3,deces:3,iz:0.65,streb:'STR-0450 URGENT',niv:'ORANGE',sa:0.70,sh:0.65,cs:0.55,str:0.70,
   kpis:{cas:'3',deces:'3',pct:'100%',score:'0.65'},
   desc:'3 zébus retrouvés morts, suspicion anthrax (charbon bactéridien). Zoonose prioritaire. Résultat STREBIAN demandé en urgence. Exposition humaine possible (éleveurs).',
   actions:[
     {cls:'act-imm',tag:'IMMÉDIAT',txt:'NE PAS nécropsier — risque spores anthrax. Enfouissement sur place'},
     {cls:'act-imm',tag:'IMMÉDIAT',txt:'Notification MSANP : exposition humaine éleveurs — antibio prophylactique'},
     {cls:'act-urg',tag:'URGENT 48h',txt:'Résultat STR-0450 prioritaire + zone cordon sanitaire 2km'},
     {cls:'act-7j',tag:'7 JOURS',txt:'Vaccination anthrax troupeaux adjacents + surveillance humaine 21j'},
   ],trends:[0,0,0,0,3]},
];

let simrSel=null, madsurSel=null;

function izColor(iz){
  if(iz>=0.70)return{bg:'#FCEBEB',col:'#A32D2D',lbl:'ROUGE',bar:'#E53935'};
  if(iz>=0.50)return{bg:'#FAEEDA',col:'#854F0B',lbl:'ORANGE',bar:'#FB8C00'};
  if(iz>=0.30)return{bg:'#FFFDE7',col:'#7a6000',lbl:'JAUNE',bar:'#FDD835'};
  return{bg:'#EAF3DE',col:'#3B6D11',lbl:'VERT',bar:'#43A047'};
}

function alertPill(a){
  const m={ROUGE:'pill-r',ORANGE:'pill-o',JAUNE:'pill-y',VERT:'pill-g'};
  return `<span class="pill ${m[a]||'pill-b'}">${a}</span>`;
}

function renderTrend(arr){
  const max=Math.max(...arr)||1;
  return arr.map(v=>{
    const h=Math.round((v/max)*28)+2;
    const pct=v/max;
    const col=pct>0.7?'#E53935':pct>0.4?'#FB8C00':'#43A047';
    return `<div style="display:inline-block;width:8px;height:${h}px;background:${col};margin-right:1px;border-radius:1px;vertical-align:bottom"></div>`;
  }).join('');
}

function scoreColor(s){
  const c=izColor(s);return c.col;
}

function buildDTA(d, type){
  const iz=type==='madsur'?(d.sa*0.30+d.sh*0.30+d.cs*0.20+d.str*0.20):(d.sa*0.25+d.sh*0.35+d.cs*0.25+d.str*0.15);
  const c=izColor(iz);
  const pct=Math.round(iz*100);
  return `<div class="dta-panel">
    <div class="dta-header">
      <i class="ti ti-analyze" aria-hidden="true"></i>
      DataToAction — ${d.id} · ${d.mal} · ${d.reg}
      <span>IZ = ${iz.toFixed(2)} | ${c.lbl}</span>
      <button class="close-btn" onclick="closeDTA('${type}')">✕ fermer</button>
    </div>
    <div class="dta-body">
      <div class="dta-kpis">
        <div class="dta-kpi"><div class="dta-kpi-lbl">${type==='madsur'?'Cas animaux':'Cas humains'}</div><div class="dta-kpi-val" style="color:#E53935">${d.kpis.cas}</div></div>
        <div class="dta-kpi"><div class="dta-kpi-lbl">Décès</div><div class="dta-kpi-val" style="color:#A32D2D">${d.kpis.deces}</div></div>
        <div class="dta-kpi"><div class="dta-kpi-lbl">${type==='madsur'?'% troupeau':'Létalité'}</div><div class="dta-kpi-val" style="color:#854F0B">${d.kpis.letal||d.kpis.pct}</div></div>
        <div class="dta-kpi"><div class="dta-kpi-lbl">Indice Zoonose</div><div class="dta-kpi-val" style="color:${c.col}">${iz.toFixed(2)}</div></div>
      </div>
      <div class="risk-bar-wrap">
        <div class="risk-label"><span>Niveau de risque global</span><span style="color:${c.col};font-weight:500">${c.lbl} — ${pct}%</span></div>
        <div class="risk-bar"><div class="risk-fill" style="width:${pct}%;background:${c.bar}"></div></div>
      </div>
      <div class="dta-grid">
        <div class="dta-block">
          <div class="dta-block-title"><i class="ti ti-paw" aria-hidden="true"></i>Signal animal (SA)<span class="score" style="color:${scoreColor(d.sa)}">${d.sa.toFixed(2)}</span></div>
          <p>${type==='madsur'?`Foyer animal confirmé. Score SA=${d.sa.toFixed(2)} basé sur cas/décès animaux, extension géographique et virulence de l'agent.`:`Signal animal associé SA=${d.sa.toFixed(2)} — surveillance MADSUR région ${d.reg} requise.`}</p>
        </div>
        <div class="dta-block">
          <div class="dta-block-title"><i class="ti ti-user-heart" aria-hidden="true"></i>Signal humain (SH)<span class="score" style="color:${scoreColor(d.sh)}">${d.sh.toFixed(2)}</span></div>
          <p>${type==='simr'?`Cas humains confirmés. Score SH=${d.sh.toFixed(2)} basé sur incidence, létalité, diffusion inter-districts et capacité riposte.`:`Risque humain associé SH=${d.sh.toFixed(2)} — signaux SIMR dans la région à corréler.`}</p>
        </div>
        <div class="dta-block">
          <div class="dta-block-title"><i class="ti ti-leaf" aria-hidden="true"></i>Environnement (CS)<span class="score" style="color:${scoreColor(d.cs)}">${d.cs.toFixed(2)}</span></div>
          <p>Facteurs environnementaux CS=${d.cs.toFixed(2)} — qualité eau, déforestation, changements climatiques locaux, vecteurs.</p>
        </div>
        <div class="dta-block">
          <div class="dta-block-title"><i class="ti ti-microscope" aria-hidden="true"></i>STREBIAN (STR)<span class="score" style="color:${scoreColor(d.str)}">${d.str.toFixed(2)}</span></div>
          <p>Confirmation laboratoire STR=${d.str.toFixed(2)}. ${type==='madsur'?d.streb:`Statut labo : ${d.str>=0.6?'Confirmé':'En cours'}.`}</p>
        </div>
      </div>
      <div class="actions-title"><i class="ti ti-list-check" aria-hidden="true" style="margin-right:4px"></i>Actions prioritaires</div>
      <div class="action-list">
        ${d.actions.map(a=>`<div class="action-item ${a.cls}"><span class="act-tag">${a.tag}</span><span>${a.txt}</span></div>`).join('')}
      </div>
      <div class="trend-mini">
        <div class="trend-label">Tendance SE18→SE22 · ${d.mal} · ${d.reg}</div>
        <div style="display:flex;align-items:flex-end;gap:6px">
          ${d.trends.map((v,i)=>{
            const max=Math.max(...d.trends)||1;
            const h=Math.round((v/max)*60)+4;
            const pct=v/max;
            const col=pct>0.7?'#E53935':pct>0.4?'#FB8C00':'#43A047';
            return `<div style="text-align:center"><div style="width:36px;height:${h}px;background:${col};border-radius:3px 3px 0 0"></div><div style="font-size:10px;color:var(--color-text-secondary);margin-top:2px">SE${18+i}</div><div style="font-size:11px;font-weight:500">${v}</div></div>`;
          }).join('')}
        </div>
      </div>
    </div>
  </div>`;
}

function closeDTA(type){
  document.getElementById(type+'-dta').style.display='none';
  document.querySelectorAll('#'+type+'-tbody tr').forEach(r=>r.classList.remove('selected'));
  if(type==='simr')simrSel=null; else madsurSel=null;
}

function renderSIMR(){
  const tb=document.getElementById('simr-tbody');
  tb.innerHTML=SIMR.map((d,i)=>`<tr class="clickable${simrSel===i?' selected':''}" onclick="selectSIMR(${i})">
    <td><strong>${d.id}</strong></td>
    <td>${d.mal}</td>
    <td>${d.reg}</td>
    <td>${d.cas}</td>
    <td>${d.deces}</td>
    <td>${d.letal}</td>
    <td><div style="display:flex;align-items:flex-end;gap:1px">${renderTrend(d.trends)}</div></td>
    <td>${alertPill(d.alerte)}</td>
    <td style="font-size:10px;color:var(--color-text-secondary)">${d.det}j/${d.notif}j/${d.rip}j</td>
  </tr>`).join('');
}

function selectSIMR(i){
  simrSel=i;
  renderSIMR();
  const el=document.getElementById('simr-dta');
  el.style.display='block';
  el.innerHTML=buildDTA(SIMR[i],'simr');
  el.scrollIntoView({behavior:'smooth',block:'nearest'});
}

function renderMADSUR(){
  const tb=document.getElementById('madsur-tbody');
  tb.innerHTML=MADSUR.map((d,i)=>{
    const c=izColor(d.iz);
    return `<tr class="clickable${madsurSel===i?' selected':''}" onclick="selectMADSUR(${i})">
      <td><strong>${d.id}</strong></td>
      <td>${d.mal}</td>
      <td>${d.reg}</td>
      <td>${d.esp}</td>
      <td>${d.cas}</td>
      <td>${d.deces}</td>
      <td><span style="font-weight:500;color:${c.col}">${d.iz.toFixed(2)}</span></td>
      <td style="font-size:10px">${d.streb}</td>
      <td>${alertPill(d.niv)}</td>
    </tr>`;
  }).join('');
}

function selectMADSUR(i){
  madsurSel=i;
  renderMADSUR();
  const el=document.getElementById('madsur-dta');
  el.style.display='block';
  el.innerHTML=buildDTA(MADSUR[i],'madsur');
  el.scrollIntoView({behavior:'smooth',block:'nearest'});
}

function showTabV5(t,el){
  // Cacher tous les panels du module-v5 uniquement
  const mod = document.getElementById('module-v5');
  if (!mod) return;
  mod.querySelectorAll('.panel').forEach(p => p.classList.remove('active'));
  mod.querySelectorAll('.tab').forEach(p => p.classList.remove('active'));
  const target = document.getElementById('tab-'+t);
  if (target) target.classList.add('active');
  // Activer le bon onglet dans la nav — el est le div.tab cliqué
  const tb = el ? el.closest('.tab') : null;
  if (tb) tb.classList.add('active');
  // Lazy init des sous-modules enrichis
  if (t === 'top5-oh' && !window._top5OHInit) { window._top5OHInit = true; renderTop5OH(); }
  if (t === 'croisee-oh' && !window._crosOHInit) { window._crosOHInit = true; renderCrosseesOH(); }
}

function buildOH(){
  const cards=document.getElementById('oh-cards');
  const convs=[
    {icon:'🐕',title:'Rage — Analamanga',sub:'MAD-01 (bovins IZ=0.85) × SIM-01 (humain ROUGE) — même foyer géographique. Transmission chien→bovin→humain documentée. Riposte conjointe GIV+MSANP active.',tags:[{l:'CRITIQUE',c:'#A32D2D',bg:'#FCEBEB'},{l:'Riposte active',c:'#185FA5',bg:'#E6F1FB'},{l:'Zoonose confirmée',c:'#3B6D11',bg:'#EAF3DE'}]},
    {icon:'🦅',title:'Influenza aviaire — Boeny',sub:'MAD-03 (H5N1 volailles IZ=0.55) × SIM-05 (IRA sévère Fianarantsoa) — lien à établir. Séquençage en cours. Surveillance passive humaine activée.',tags:[{l:'SURVEILLER',c:'#854F0B',bg:'#FAEEDA'},{l:'PCR en cours',c:'#185FA5',bg:'#E6F1FB'}]},
    {icon:'💧',title:'Leptospirose — Boeny',sub:'MAD-02 (bovin eau/leptospirose) × SIM-06 (leptospirose humaine Mahajanga) × MEEF inondation — triplé One Health eau/animal/humain. Investigation croisée DSV+MSANP+MEEF.',tags:[{l:'ONE HEALTH',c:'#0F1F5C',bg:'#E8EDFF'},{l:'Environnemental',c:'#3B6D11',bg:'#EAF3DE'}]},
  ];
  cards.innerHTML=convs.map(c=>`<div class="conv-card">
    <div class="conv-icon" style="background:var(--color-background-secondary)">${c.icon}</div>
    <div class="conv-body">
      <div class="conv-title">${c.title}</div>
      <div class="conv-sub">${c.sub}</div>
      <div class="conv-tags">${c.tags.map(t=>`<span class="pill" style="background:${t.bg};color:${t.c}">${t.l}</span>`).join('')}</div>
    </div>
  </div>`).join('');

  const hItems=['Rage humaine (3 cas, 1 décès) — ROUGE','MPox DIANA (2 cas confirmés) — ROUGE','Paludisme grave SAVA (18 cas) — ORANGE','Choléra suspect Toamasina — ORANGE','IRA sévère cluster Fianarantsoa — JAUNE','Leptospirose Mahajanga (4 cas) — JAUNE'];
  const aItems=['Rage bovine Analamanga (IZ=0.85) — ROUGE','Influenza aviaire H5N1 Boeny (IZ=0.55) — ORANGE','Anthrax suspect Melaky (IZ=0.65) — ORANGE','Leptospirose bovine Boeny (IZ=0.42) — JAUNE','FMD Vakinankaratra (IZ=0.38) — JAUNE'];
  const eItems=['Inondations côtières Toamasina — risque leptospirose/choléra','Déforestation Melaky — risque anthrax sporadique','Saison pluies SAVA — amplification vecteurs paludisme','Marchés volailles Boeny — transmission H5N1'];

  document.getElementById('oh-h').innerHTML=hItems.map(i=>`<div class="oh-item">${i}</div>`).join('');
  document.getElementById('oh-a').innerHTML=aItems.map(i=>`<div class="oh-item">${i}</div>`).join('');
  document.getElementById('oh-e').innerHTML=eItems.map(i=>`<div class="oh-item">${i}</div>`).join('');
}

function buildBulletin(){
  const secs=[
    {title:'Signaux ROUGE actifs',icon:'ti-alert-triangle',col:'#A32D2D',items:['SIM-01 Rage humaine Analamanga (3 cas, 1 décès)','SIM-02 MPox DIANA (2 cas PCR+)','MAD-01 Rage bovine Analamanga (IZ=0.85)']},
    {title:'Signaux ORANGE',icon:'ti-alert-circle',col:'#854F0B',items:['SIM-03 Paludisme grave SAVA (18 cas)','MAD-03 Influenza aviaire H5N1 Boeny','MAD-05 Anthrax suspect Melaky']},
    {title:'Indicateurs 7-1-7',icon:'ti-clock',col:'#185FA5',items:['Détection moy. : 4.8j ✓ (cible ≤7j)','Notification : 1.2j ✓ (cible ≤1j)','Riposte initiée : 5.1j ✓ (cible ≤7j)']},
    {title:'STREBIAN SE 22',icon:'ti-microscope',col:'#0F1F5C',items:['STR-0441 POSITIF H5N1 (Boeny)','STR-0442 POSITIF Rage (Analamanga)','STR-0445 EN COURS (Boeny/Leptospirose)','STR-0450 URGENT (Melaky/Anthrax)']},
  ];
  document.getElementById('bulletin-sections').innerHTML=secs.map(s=>`<div style="border:0.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-md);padding:12px">
    <div style="font-size:12px;font-weight:500;color:${s.col};margin-bottom:8px"><i class="ti ${s.icon}" aria-hidden="true" style="margin-right:5px"></i>${s.title}</div>
    ${s.items.map(i=>`<div style="font-size:11px;color:var(--color-text-primary);padding:3px 0;border-bottom:0.5px solid var(--color-border-tertiary)">${i}</div>`).join('')}
  </div>`).join('');
}

renderSIMR();
renderMADSUR();
buildOH();
buildBulletin();
</script>

</div>

<script>
function switchModule(id) {
  document.querySelectorAll('.sbesoh-module').forEach(m => { m.style.display='none'; m.classList.remove('active'); });
  document.querySelectorAll('.module-tab').forEach(t => t.classList.remove('active'));
  document.getElementById('module-'+id).style.display='block';
  document.getElementById('module-'+id).classList.add('active');
  event.currentTarget.classList.add('active');
  // Lazy map drawing
  if (id === 'carto' && typeof cartoMapDrawn !== 'undefined' && !cartoMapDrawn) {
    setTimeout(drawCartoMap, 50);
  }
}
</script>

<script>
// ══════════════════════════════════════════════════════════════
// SIMR SOUS-ONGLETS
// ══════════════════════════════════════════════════════════════
function showSIMRTab(id, el) {
  document.querySelectorAll('.simr-stab-content').forEach(t => t.style.display = 'none');
  document.querySelectorAll('.simr-stab').forEach(t => {
    t.style.borderBottomColor = 'transparent';
    t.style.color = 'var(--color-text-secondary)';
    t.style.fontWeight = '400';
  });
  const tab = document.getElementById('simr-tab-' + id);
  if (tab) tab.style.display = 'block';
  if (el) {
    el.style.borderBottomColor = '#0F1F5C';
    el.style.color = 'var(--color-text-primary)';
    el.style.fontWeight = '500';
  }
  // Lazy init charts
  if (id === 'tendances' && !window._simrTrendInit) { window._simrTrendInit = true; initTrendCharts(); }
  if (id === 'performance' && !window._simrPerfInit) { window._simrPerfInit = true; initPerfCharts(); }
  if (id === 'zoonoses-ihr' && !window._simrIHRInit) { window._simrIHRInit = true; initIHR(); }
  if (id === 'par-region' && !window._simrRegInit) { window._simrRegInit = true; initRegionCharts(); }
}

// ── TENDANCES ──────────────────────────────────────────────────
function initTrendCharts() {
  const se = ['SE18','SE19','SE20','SE21','SE22'];
  new Chart(document.getElementById('trend-zoonoses'), {
    type:'line',
    data:{ labels:se, datasets:[
      {label:'Rage', data:[0,0,0,0,1], borderColor:'#B71C1C', backgroundColor:'rgba(183,28,28,0.07)', fill:true, tension:0.3, pointRadius:4},
      {label:'MPox', data:[3,2,4,4,7], borderColor:'#E65100', backgroundColor:'rgba(230,81,0,0.07)', fill:false, tension:0.3, pointRadius:4},
      {label:'Leptospirose', data:[22,28,35,31,54], borderColor:'#006064', backgroundColor:'rgba(0,96,100,0.07)', fill:false, tension:0.3, pointRadius:4},
    ]},
    options:{ responsive:true, maintainAspectRatio:false, plugins:{ legend:{ display:true, labels:{ font:{size:9}, boxWidth:10 } } }, scales:{ x:{ticks:{font:{size:9}}}, y:{ticks:{font:{size:9}}, beginAtZero:true} } }
  });
  new Chart(document.getElementById('trend-vectorielles'), {
    type:'line',
    data:{ labels:se, datasets:[
      {label:'Paludisme', data:[245,278,312,251,312], borderColor:'#1565C0', backgroundColor:'rgba(21,101,192,0.07)', fill:true, tension:0.3, pointRadius:4},
      {label:'Dengue (susp.)', data:[5,6,9,8,14], borderColor:'#E65100', backgroundColor:'rgba(230,81,0,0.07)', fill:false, tension:0.3, pointRadius:4, borderDash:[4,2]},
    ]},
    options:{ responsive:true, maintainAspectRatio:false, plugins:{ legend:{ display:true, labels:{ font:{size:9}, boxWidth:10 } } }, scales:{ x:{ticks:{font:{size:9}}}, y:{ticks:{font:{size:9}}, beginAtZero:true} } }
  });
  new Chart(document.getElementById('trend-enteriques'), {
    type:'line',
    data:{ labels:se, datasets:[
      {label:'Diarrhée', data:[215,198,210,225,198], borderColor:'#558B2F', backgroundColor:'rgba(85,139,47,0.07)', fill:true, tension:0.3, pointRadius:4},
      {label:'GEA', data:[75,82,91,95,89], borderColor:'#8BC34A', backgroundColor:'rgba(139,195,74,0.07)', fill:false, tension:0.3, pointRadius:3, borderDash:[4,2]},
      {label:'Choléra (susp.)', data:[0,0,2,0,11], borderColor:'#B71C1C', backgroundColor:'rgba(183,28,28,0.07)', fill:false, tension:0.3, pointRadius:4},
    ]},
    options:{ responsive:true, maintainAspectRatio:false, plugins:{ legend:{ display:true, labels:{ font:{size:9}, boxWidth:10 } } }, scales:{ x:{ticks:{font:{size:9}}}, y:{ticks:{font:{size:9}}, beginAtZero:true} } }
  });
  new Chart(document.getElementById('trend-global'), {
    type:'bar',
    data:{ labels:se, datasets:[
      {label:'Cas SIMR total', data:[980,1050,1134,1149,1247], backgroundColor:['#85B7EB','#85B7EB','#85B7EB','#85B7EB','#0F1F5C'], borderRadius:3},
      {label:'Décès', data:[9,11,13,12,14], backgroundColor:'rgba(183,28,28,0.75)', borderRadius:3},
    ]},
    options:{ responsive:true, maintainAspectRatio:false, plugins:{ legend:{ display:true, labels:{ font:{size:10}, boxWidth:10 } } }, scales:{ x:{ticks:{font:{size:10}}}, y:{ticks:{font:{size:10}}, beginAtZero:true} } }
  });
}

// ── PERFORMANCE ────────────────────────────────────────────────
function initPerfCharts() {
  // 7-1-7 par signal
  const p717data = [
    {sig:'SIM-01 Rage', det:3, notif:1, rip:5, al:'#B71C1C'},
    {sig:'SIM-02 MPox', det:5, notif:1, rip:3, al:'#B71C1C'},
    {sig:'SIM-03 Palu.grave', det:4, notif:1, rip:6, al:'#F57F17'},
    {sig:'SIM-04 Choléra', det:6, notif:1, rip:4, al:'#F57F17'},
    {sig:'SIM-05 IRA sévère', det:7, notif:2, rip:7, al:'#F9E06E'},
    {sig:'SIM-06 Lepto.', det:5, notif:2, rip:8, al:'#F9E06E'},
    {sig:'SIM-07 Leishm.', det:8, notif:2, rip:0, al:'#E8F5E9'},
  ];
  const el717 = document.getElementById('perf-717');
  el717.innerHTML = p717data.map(p => {
    const detC = p.det<=7?'#1B5E20':'#B71C1C'; const ripC = p.rip>0&&p.rip<=7?'#1B5E20':'#B71C1C';
    return `<div style="border-radius:5px;padding:7px 9px;background:var(--color-background-secondary);border-left:3px solid ${p.al};">
      <div style="font-size:10px;font-weight:500;margin-bottom:4px;">${p.sig}</div>
      <div style="display:flex;gap:8px;font-size:10px;">
        <span style="color:${detC};">Détect: <strong>${p.det}j</strong></span>
        <span style="color:#185FA5;">Notif: <strong>${p.notif}j</strong></span>
        <span style="color:${p.rip>0?ripC:'#999'};">${p.rip>0?'Rip: <strong>'+p.rip+'j</strong>':'Riposte: —'}</span>
      </div>
    </div>`;
  }).join('');

  // CFR chart
  new Chart(document.getElementById('cfr-chart'), {
    type:'bar', indexAxis:'y',
    data:{ labels:['Rage','TB','Palu.grave','Méning.','IRA','Lepto.','Palu.','Typhoïde','Choléra','MPox','GEA'],
      datasets:[{ data:[100,4.6,4.2,4.3,11,3.7,0.6,0,0,0,0],
        backgroundColor:['#B71C1C','#546E7A','#B71C1C','#E65100','#E65100','#F57F17','#4CAF50','#4CAF50','#4CAF50','#4CAF50','#4CAF50'],
        borderRadius:3 }] },
    options:{ responsive:true, maintainAspectRatio:false, plugins:{legend:{display:false}},
      scales:{ x:{ticks:{font:{size:9}}, title:{display:true,text:'CFR (%)',font:{size:9}}}, y:{ticks:{font:{size:9}}} } }
  });

  // Complétude par région top 8
  const compl = [
    {r:'Analamanga',p:84},{r:'Atsinanana',p:81},{r:'Boeny',p:78},{r:'Alaotra-Mangoro',p:75},
    {r:'Itasy',p:76},{r:'Vakinankaratra',p:72},{r:'Betsiboka',p:70},{r:'Analanjirofo',p:69},
    {r:'Haute Matsiatra',p:68},{r:'Sofia',p:65},
  ];
  const elC = document.getElementById('perf-completude');
  elC.innerHTML = compl.map(c => {
    const col = c.p>=75?'#1B5E20':c.p>=60?'#F57F17':'#B71C1C';
    return `<div style="display:flex;align-items:center;gap:8px;">
      <span style="font-size:10px;min-width:130px;">${c.r}</span>
      <div style="flex:1;background:var(--color-background-tertiary);border-radius:3px;height:7px;overflow:hidden;"><div style="width:${c.p}%;height:100%;background:${col};border-radius:3px;"></div></div>
      <span style="font-size:10px;font-weight:600;color:${col};min-width:30px;text-align:right;">${c.p}%</span>
    </div>`;
  }).join('');

  // Donut catégories
  new Chart(document.getElementById('cat-pie'), {
    type:'doughnut',
    data:{ labels:['Vectorielles','Respiratoires','Gastro-entériques','Zoonoses','Neurologiques'],
      datasets:[{ data:[374,310,298,66,23],
        backgroundColor:['#1565C0','#546E7A','#558B2F','#B71C1C','#4A148C'],
        borderWidth:2, borderColor:'#fff' }] },
    options:{ responsive:true, maintainAspectRatio:false,
      plugins:{ legend:{ display:true, position:'right', labels:{ font:{size:9}, boxWidth:10 } } } }
  });

  // Districts en riposte
  const rip = [
    {d:'Anjozorobe (Analamanga)',mal:'Rage zoonose OH',al:'#B71C1C',j:3},
    {d:'Antsiranana (DIANA)',mal:'MPox',al:'#B71C1C',j:1},
    {d:'Sambava (SAVA)',mal:'Paludisme grave',al:'#F57F17',j:6},
    {d:'Toamasina (Atsinanana)',mal:'Choléra suspect',al:'#F57F17',j:4},
    {d:'Mahajanga (Boeny)',mal:'Leptospirose',al:'#F9E06E',j:8},
    {d:'Fianarantsoa (HM)',mal:'IRA sévère cluster',al:'#F9E06E',j:7},
    {d:'Mandritsara (Sofia)',mal:'Paludisme',al:'#4CAF50',j:5},
  ];
  document.getElementById('riposte-list').innerHTML = rip.map(r =>
    `<div style="display:flex;align-items:center;gap:8px;padding:6px 8px;background:var(--color-background-secondary);border-radius:5px;border-left:3px solid ${r.al};">
      <div style="flex:1;">
        <div style="font-size:11px;font-weight:500;">${r.d}</div>
        <div style="font-size:10px;color:var(--color-text-secondary);">${r.mal}</div>
      </div>
      <div style="text-align:right;"><div style="font-size:10px;font-weight:600;color:${r.al};">J+${r.j}/7-1-7</div></div>
    </div>`
  ).join('');
}

// ── ZOONOSES & IHR ────────────────────────────────────────────
function initIHR() {
  const zList = [
    {agent:'Virus rage (RABV)', cas:'1 cas + 3 susp.', streb:'POSITIF STR-0442', ihr:'ART.12 — Notif. requise', ihrc:'#B71C1C'},
    {agent:'Monkeypox (MPox)', cas:'7 cas confirmés', streb:'Non initié', ihr:'Surveillance IHR active', ihrc:'#E65100'},
    {agent:'Influenza A/H5N1', cas:'0 cas humains', streb:'POSITIF STR-0441', ihr:'Notif. OIE/FAO — veille RSI', ihrc:'#E65100'},
    {agent:'Leptospira spp.', cas:'54 cas CFR 3.7%', streb:'EN COURS STR-0445', ihr:'Pas de notif. requise', ihrc:'#4CAF50'},
    {agent:'Brucella spp.', cas:'4 cas suspects', streb:'EN COURS STR-0446', ihr:'Pas de notif. requise', ihrc:'#4CAF50'},
    {agent:'Bacillus anthracis', cas:'0 cas humains', streb:'URGENT STR-0450', ihr:'À évaluer si confirmé', ihrc:'#F57F17'},
  ];
  const tb = document.getElementById('zoonoses-ihr-tbody');
  tb.innerHTML = zList.map((z,i) => `<tr style="border-bottom:.5px solid var(--color-border-tertiary);${i%2===0?'background:var(--color-background-secondary);':''}">
    <td style="padding:5px 8px;font-weight:500;">${z.agent}</td>
    <td style="padding:5px 8px;">${z.cas}</td>
    <td style="padding:5px 8px;"><span style="font-size:9px;padding:1px 6px;border-radius:3px;background:${z.streb.startsWith('POSITIF')?'#FFCDD2':z.streb.startsWith('EN COURS')?'#FFF9C4':z.streb.includes('URGENT')?'#FFCDD2':'var(--color-background-secondary)'};color:${z.streb.startsWith('POSITIF')?'#B71C1C':z.streb.includes('URGENT')?'#B71C1C':'#F57F17'};font-weight:500;">${z.streb}</span></td>
    <td style="padding:5px 8px;"><span style="font-size:9px;padding:1px 6px;border-radius:3px;background:${z.ihrc+'22'};color:${z.ihrc};font-weight:500;">${z.ihr}</span></td>
  </tr>`).join('');

  // IHR décision
  const ihr = [
    {mal:'Rage humaine', yes:true, txt:'Art. 12 RSI : événement grave, inattendu, risque propagation internationale — Notification OMS dans les 24h requise', col:'#B71C1C'},
    {mal:'MPox', yes:false, txt:'Surveillance active. Si ≥3 nouvelles régions ou lien source animale confirmé → notification Art. 12. Alerte Africa CDC maintenue.', col:'#E65100'},
    {mal:'Influenza A/H5N1', yes:false, txt:'Pas de cas humain à ce jour. Notification OIE/FAO en cours. Si cas humain confirmé → notification RSI immédiate.', col:'#F57F17'},
  ];
  document.getElementById('ihr-decision-list').innerHTML = ihr.map(i =>
    `<div style="border-radius:6px;padding:9px 11px;background:${i.col+'18'};border-left:3px solid ${i.col};">
      <div style="font-size:11px;font-weight:600;color:${i.col};margin-bottom:3px;">
        ${i.mal} — ${i.yes?'&#9989; Notif. RSI requise':'&#8987; Évaluation en cours'}
      </div>
      <div style="font-size:10px;color:var(--color-text-primary);line-height:1.5;">${i.txt}</div>
    </div>`
  ).join('');

  // Chaînes de transmission
  const chains = [
    {title:'Rage — Anjozorobe',icon:'🐕', chain:'Chien errant → Bovins (mortalité 67%) → Humain (morsure) → 1 décès confirmé', col:'#B71C1C', actions:'PEP dans les 24h · VAR canine · Abattage bovins suspects'},
    {title:'Leptospirose — Boeny',icon:'💧', chain:'Rongeurs → Eau de crue → Bovins (MAD-02) + Humains (SIM-06) simultanément', col:'#006064', actions:'Investigation eau commune · EPI agents terrain · Doxycycline prophy'},
    {title:'MPox — Analamanga', icon:'🦠', chain:'Réservoir animal non identifié (rongeurs ?) → Contact humain direct → Cluster marché Isotry (3 cas)', col:'#E65100', actions:'Traçage contacts · Isolement · Génotypage CNRE'},
    {title:'H5N1 — Boeny', icon:'🦅', chain:'Oiseaux migrateurs ? → Volailles élevages (340 cas, létalité 82%) → Humain : 0 cas à ce jour', col:'#F57F17', actions:'Abattage + biosécurité · Surveillance IRA humaine 20km'},
  ];
  document.getElementById('transmission-chains').innerHTML = chains.map(c =>
    `<div style="border-radius:7px;padding:10px 12px;background:var(--color-background-secondary);border-top:3px solid ${c.col};">
      <div style="font-size:12px;font-weight:600;margin-bottom:4px;">${c.icon} ${c.title}</div>
      <div style="font-size:11px;color:var(--color-text-primary);line-height:1.5;margin-bottom:5px;">${c.chain}</div>
      <div style="font-size:10px;color:${c.col};font-weight:500;background:${c.col+'18'};border-radius:4px;padding:4px 7px;">${c.actions}</div>
    </div>`
  ).join('');
}

// ── PAR RÉGION ─────────────────────────────────────────────────
function initRegionCharts() {
  const regData = [
    {r:'Boeny',cas:312,al:'#E65100'},{r:'Analamanga',cas:298,al:'#B71C1C'},
    {r:'Atsinanana',cas:187,al:'#F57F17'},{r:'Vakinankaratra',cas:142,al:'#F57F17'},
    {r:'Sofia',cas:89,al:'#F9E06E'},{r:'GEA/Autres',cas:89,al:'#4CAF50'},
    {r:'Alaotra-Mang.',cas:76,al:'#4CAF50'},{r:'Analanjirofo',cas:29,al:'#4CAF50'},
    {r:'Bongolava',cas:22,al:'#4CAF50'},{r:'DIANA',cas:61,al:'#F57F17'},
    {r:'SAVA',cas:47,al:'#4CAF50'},
  ];
  new Chart(document.getElementById('region-chart'), {
    type:'bar',
    data:{ labels:regData.map(r=>r.r), datasets:[{ label:'Cas SIMR SE22', data:regData.map(r=>r.cas),
      backgroundColor:regData.map(r=>r.al), borderRadius:4 }] },
    options:{ responsive:true, maintainAspectRatio:false, plugins:{legend:{display:false}},
      scales:{ x:{ticks:{font:{size:9},autoSkip:false,maxRotation:30}}, y:{ticks:{font:{size:9}},beginAtZero:true} } }
  });
  const top5r = [{r:'Boeny',cas:312,mal:'Paludisme',sig:'4 MADSUR'},{r:'Analamanga',cas:298,mal:'Rage+MPox',sig:'5 MADSUR'},{r:'Atsinanana',cas:187,mal:'Leptospirose',sig:'3 MADSUR'},{r:'Vakinankaratra',cas:142,mal:'Brucellose/IRA',sig:'4 MADSUR'},{r:'DIANA',cas:61,mal:'MPox+Dengue',sig:'0 MADSUR'}];
  document.getElementById('region-top5-list').innerHTML = top5r.map((r,i) =>
    `<div style="display:flex;align-items:center;gap:8px;padding:6px 8px;background:var(--color-background-secondary);border-radius:5px;">
      <span style="font-size:11px;font-weight:700;color:#0F1F5C;min-width:16px;">#${i+1}</span>
      <div style="flex:1;"><div style="font-size:11px;font-weight:500;">${r.r}</div><div style="font-size:10px;color:var(--color-text-secondary);">${r.mal} · ${r.sig}</div></div>
      <span style="font-size:12px;font-weight:700;color:#0F1F5C;">${r.cas}</span>
    </div>`
  ).join('');
  const multi = [{r:'Boeny',sigs:'Paludisme + Leptospirose + H5N1 + Choléra',n:4},{r:'Analamanga',sigs:'Rage humaine + MPox + IRA',n:3},{r:'Atsinanana',sigs:'Leptospirose + MPox + Choléra suspect',n:3},{r:'Vakinankaratra',sigs:'Brucellose + IRA + FMD (MADSUR)',n:3}];
  document.getElementById('region-multi-list').innerHTML = multi.map(m =>
    `<div style="padding:7px 9px;background:#FFF3E0;border-radius:6px;border-left:3px solid #E65100;">
      <div style="font-size:11px;font-weight:600;margin-bottom:2px;">${m.r} — <span style="color:#B71C1C;">${m.n} signaux actifs</span></div>
      <div style="font-size:10px;color:var(--color-text-secondary);">${m.sigs}</div>
    </div>`
  ).join('');
}

// ══════════════════════════════════════════════════════════════
// TOP5 + CROISÉE dans Intégré OH (v5)
// ══════════════════════════════════════════════════════════════
function renderTop5OH() {
  const top5d = [
    {rang:1,mal:'Rage humaine / bovine',reg:'Analamanga',why:'Zoonose confirmée, décès humain, IZ=0.85. Foyer OH actif.',al:'ROUGE',col:'#B71C1C',bg:'#FFEBEE',actions:'PEP immédiat · VAR canine · équipe OH'},
    {rang:2,mal:'MPox',reg:'5 régions',why:'Progression nationale +75%. Clade II. Réservoir inconnu.',al:'ROUGE',col:'#B71C1C',bg:'#FFEBEE',actions:'Traçage contacts · Génotypage CNRE'},
    {rang:3,mal:'Influenza aviaire H5N1',reg:'Boeny',why:'Létalité 82% volailles. STR POSITIF. Risque pandémique à surveiller.',al:'ORANGE',col:'#E65100',bg:'#FFF3E0',actions:'Abattage · OIE · surveillance humaine'},
    {rang:4,mal:'Anthrax suspect',reg:'Melaky',why:'Zoonose grave, IZ=0.65. Exposition humaine possible. STR urgent.',al:'ORANGE',col:'#E65100',bg:'#FFF3E0',actions:'STR-0450 prioritaire · cordon 2km'},
    {rang:5,mal:'Paludisme grave',reg:'SAVA',why:'Dépasse seuil épidémique. 2 décès <5 ans. Rupture ACT.',al:'ORANGE',col:'#E65100',bg:'#FFF3E0',actions:'Réappro ACT urgente · MILD'},
  ];
  const el = document.getElementById('top5-oh-cards');
  if (!el) return;
  el.innerHTML = top5d.map(t =>
    `<div style="border-radius:7px;padding:10px 13px;background:${t.bg};border-left:4px solid ${t.col};border:.5px solid ${t.col}44;">
      <div style="display:flex;align-items:flex-start;justify-content:space-between;gap:10px;">
        <div>
          <div style="display:flex;align-items:center;gap:6px;margin-bottom:4px;">
            <span style="background:${t.col};color:#fff;font-size:10px;font-weight:700;width:20px;height:20px;border-radius:50%;display:inline-flex;align-items:center;justify-content:center;">${t.rang}</span>
            <span style="font-size:13px;font-weight:600;color:var(--color-text-primary);">${t.mal}</span>
            <span style="font-size:9px;color:var(--color-text-secondary);">${t.reg}</span>
          </div>
          <div style="font-size:11px;color:var(--color-text-secondary);line-height:1.5;margin-bottom:5px;">${t.why}</div>
          <div style="font-size:10px;color:${t.col};font-weight:500;background:${t.col}18;border-radius:3px;padding:3px 8px;display:inline-block;">${t.actions}</div>
        </div>
        <span style="background:${t.col};color:#fff;font-size:9px;font-weight:700;padding:2px 8px;border-radius:3px;white-space:nowrap;flex-shrink:0;">${t.al}</span>
      </div>
    </div>`
  ).join('');

  // Risk matrix OH
  const rmOH = document.getElementById('risk-matrix-oh');
  if (rmOH && typeof Chart !== 'undefined') {
    new Chart(rmOH, {
      type:'bubble',
      data:{ datasets:[
        {label:'Rage',data:[{x:1.5,y:4.9,r:8}],backgroundColor:'rgba(183,28,28,0.75)'},
        {label:'MPox',data:[{x:3.2,y:3.8,r:10}],backgroundColor:'rgba(183,28,28,0.75)'},
        {label:'Paludisme',data:[{x:3.8,y:4.2,r:14}],backgroundColor:'rgba(21,101,192,0.75)'},
        {label:'Leptospirose',data:[{x:3.5,y:3.5,r:9}],backgroundColor:'rgba(0,96,100,0.75)'},
        {label:'Choléra',data:[{x:2.2,y:4.5,r:7}],backgroundColor:'rgba(74,20,140,0.75)'},
        {label:'IRA',data:[{x:4.5,y:2.0,r:12}],backgroundColor:'rgba(84,110,122,0.6)'},
        {label:'Anthrax',data:[{x:1.2,y:4.8,r:7}],backgroundColor:'rgba(230,81,0,0.75)'},
        {label:'H5N1 av.',data:[{x:2.5,y:4.0,r:6}],backgroundColor:'rgba(230,81,0,0.75)'},
      ]},
      options:{ responsive:true, maintainAspectRatio:false, plugins:{ legend:{display:false}, tooltip:{callbacks:{label:ctx=>`${ctx.dataset.label}`}} },
        scales:{ x:{min:0,max:5.5,title:{display:true,text:'Probabilité →',font:{size:10}},ticks:{font:{size:9}}}, y:{min:0,max:5.5,title:{display:true,text:'Impact →',font:{size:10}},ticks:{font:{size:9}}} } }
    });
    const rlOH = document.getElementById('risk-legend-oh');
    if (rlOH) [['#B71C1C','Rage/MPox'],['#1565C0','Paludisme'],['#006064','Leptospirose'],['#4A148C','Choléra'],['#E65100','Anthrax/H5N1'],['#546E7A','IRA']].forEach(([c,l]) => {
      rlOH.innerHTML += `<span style="display:flex;align-items:center;gap:3px;"><span style="width:9px;height:9px;border-radius:50%;background:${c};display:inline-block;"></span>${l}</span>`;
    });
  }
}

function renderCrosseesOH() {
  const crossOH = document.getElementById('cross-signals-oh');
  if (!crossOH) return;
  const cs = [
    {title:'Rage zoonose — Anjozorobe',level:'ROUGE CRITIQUE',col:'#B71C1C',bg:'#FFEBEE',body:'MAD-01 rage bovine (IZ=0.85) × SIM-01 rage humaine (1 décès) — même foyer géographique. Chien errant comme vecteur pont. Riposte One Health GIV+MSANP+DSV active.',action:'Équipe OH mobilisée J3 · Campagne VAR · PEP 100% contacts · Notification IHR Art.12'},
    {title:'H5N1 Boeny × IRA Fianarantsoa',level:'SURVEILLER',col:'#E65100',bg:'#FFF3E0',body:'MAD-03 influenza aviaire H5N1 (Boeny) × SIM-05 IRA sévère cluster (Fianarantsoa, 9 cas). Lien inter-espèces non confirmé — séquençage prioritaire. Distance géo : 420 km.',action:'PCR H5 sur 3 cas IRA sévères · Surveillance active humaine dans rayon 20km foyer aviaire'},
    {title:'Leptospirose — Interface eau/animal/humain',level:'ONE HEALTH',col:'#006064',bg:'#E0F7FA',body:'MAD-02 leptospirose bovine (Boeny) × SIM-06 leptospirose humaine (Mahajanga) × inondations côtières MEEF — triplé One Health confirmé. Même source eau probable.',action:'Investigation conjointe DSV+MSANP+MEEF · EPI agents terrain · Doxycycline prophylactique'},
    {title:'Anthrax Melaky — Risque exposition humaine',level:'URGENT',col:'#E65100',bg:'#FFF3E0',body:'MAD-05 anthrax suspect (3 zébus morts, IZ=0.65) × éleveurs exposés. STR-0450 résultat urgent. Zone agricole isolée, accès difficile.',action:'Cordon sanitaire 2km · Antibio prophylactique éleveurs · Ne pas nécropsier · STR 24h'},
  ];
  crossOH.innerHTML = cs.map(c =>
    `<div style="border-radius:7px;padding:10px 13px;background:${c.bg};border-left:4px solid ${c.col};">
      <div style="display:flex;align-items:center;gap:8px;margin-bottom:5px;">
        <span style="font-size:12px;font-weight:600;color:var(--color-text-primary);">${c.title}</span>
        <span style="background:${c.col};color:#fff;font-size:9px;font-weight:700;padding:1px 7px;border-radius:3px;margin-left:auto;white-space:nowrap;">${c.level}</span>
      </div>
      <div style="font-size:11px;color:var(--color-text-secondary);line-height:1.5;margin-bottom:6px;">${c.body}</div>
      <div style="font-size:10px;color:${c.col};font-weight:500;background:${c.col}18;border-radius:4px;padding:4px 8px;">${c.action}</div>
    </div>`
  ).join('');

  // Charts convergence-chart-oh
  const ccOH = document.getElementById('convergence-chart-oh');
  if (ccOH && typeof Chart !== 'undefined') {
    new Chart(ccOH, {type:'bar',
      data:{labels:['Analamanga','Boeny','Vaki.','Atsinanana','Sofia'],datasets:[
        {label:'Cas humains SIMR',data:[298,312,142,187,89],backgroundColor:'rgba(15,31,92,0.7)'},
        {label:'Signaux MADSUR ×20',data:[100,80,80,60,60],backgroundColor:'rgba(0,96,100,0.7)'},
      ]},
      options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{display:true,labels:{font:{size:9},boxWidth:10}}},scales:{x:{ticks:{font:{size:9},autoSkip:false}},y:{ticks:{font:{size:9}}}}}
    });
  }
  const tlOH = document.getElementById('timeline-chart-oh');
  if (tlOH && typeof Chart !== 'undefined') {
    new Chart(tlOH, {type:'line',
      data:{labels:['SE18','SE19','SE20','SE21','SE22'],datasets:[
        {label:'Cas SIMR /10',data:[98,105,134,115,125],borderColor:'#0F1F5C',backgroundColor:'rgba(15,31,92,0.07)',fill:true,tension:0.3,pointRadius:3},
        {label:'Signaux MADSUR',data:[12,14,18,20,23],borderColor:'#006064',backgroundColor:'rgba(0,96,100,0.07)',fill:true,tension:0.3,pointRadius:3,borderDash:[4,2]},
      ]},
      options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{display:true,labels:{font:{size:9},boxWidth:10}}},scales:{x:{ticks:{font:{size:9},autoSkip:false}},y:{ticks:{font:{size:9}}}}}
    });
  }

  // Zoonose-tbody-oh
  const ztOH = document.getElementById('zoonose-tbody-oh');
  if (ztOH) {
    const zz=[
      {agent:'Virus rage (RABV)',human:'1 cas mordu, 1 décès',animal:'Bovins — mortalité 8%',zone:'Anjozorobe/Analamanga',streb:'POSITIF (STR-0442)',prio:'CRITIQUE'},
      {agent:'Leptospira spp.',human:'54 cas, CFR 3.7%',animal:'Bovins Boeny (STR-0445)',zone:'Atsinanana, Boeny',streb:'EN COURS',prio:'HAUTE'},
      {agent:'MPox (MPXV)',human:'7 cas confirmés',animal:'Réservoir non testé',zone:'5 régions',streb:'Non initié',prio:'HAUTE'},
      {agent:'Brucella spp.',human:'4 cas suspects',animal:'Bovins Vakinankaratra',zone:'Vakinankaratra',streb:'EN COURS STR-0446',prio:'MODÉRÉE'},
      {agent:'Influenza A/H5N1',human:'0 cas humains',animal:'Volailles Boeny (STR+)',zone:'Boeny',streb:'POSITIF STR-0441',prio:'MODÉRÉE'},
      {agent:'Bacillus anthracis',human:'0 cas (exposition éleveurs)',animal:'Zébus Melaky',zone:'Melaky',streb:'URGENT STR-0450',prio:'HAUTE'},
    ];
    const pBg={CRITIQUE:'#FFCDD2',HAUTE:'#FFE0B2',MODÉRÉE:'#FFF9C4'};
    const pTxt={CRITIQUE:'#B71C1C',HAUTE:'#E65100',MODÉRÉE:'#F57F17'};
    ztOH.innerHTML = zz.map((z,i)=>`<tr style="border-bottom:.5px solid var(--color-border-tertiary);${i%2===0?'background:var(--color-background-secondary);':''}">
      <td style="padding:5px 8px;font-weight:500;">${z.agent}</td>
      <td style="padding:5px 8px;">${z.human}</td>
      <td style="padding:5px 8px;">${z.animal}</td>
      <td style="padding:5px 8px;font-size:10px;color:var(--color-text-secondary);">${z.zone}</td>
      <td style="text-align:center;padding:5px 8px;"><span style="background:${z.streb.startsWith('POSITIF')?'#FFCDD2':z.streb==='Non initié'?'var(--color-background-secondary)':z.streb.includes('URGENT')?'#FFCDD2':'#FFF9C4'};color:${z.streb.startsWith('POSITIF')||z.streb.includes('URGENT')?'#B71C1C':z.streb==='Non initié'?'var(--color-text-secondary)':'#F57F17'};font-size:9px;padding:1px 6px;border-radius:3px;">${z.streb}</span></td>
      <td style="text-align:center;padding:5px 8px;"><span style="background:${pBg[z.prio]||'#E8F5E9'};color:${pTxt[z.prio]||'#1B5E20'};font-size:9px;padding:2px 7px;border-radius:3px;font-weight:500;">${z.prio}</span></td>
    </tr>`).join('');
  }
}

// lazy init géré directement dans showTabV5 ci-dessous
</script>

</body>
</html>

