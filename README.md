<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CCP-CNS2026 — Problem 1</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;600&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --navy: #0d1b2a;
    --navy2: #1b2d42;
    --navy3: #243447;
    --blue: #2563eb;
    --blue-light: #3b82f6;
    --cyan: #06b6d4;
    --cyan-dim: #0e7490;
    --green: #22c55e;
    --amber: #f59e0b;
    --red: #ef4444;
    --text: #e2e8f0;
    --text-dim: #94a3b8;
    --text-muted: #64748b;
    --border: rgba(148,163,184,0.12);
    --border-bright: rgba(148,163,184,0.25);
    --card: rgba(255,255,255,0.04);
    --card-hover: rgba(255,255,255,0.07);
    --mono: 'JetBrains Mono', monospace;
    --sans: 'Syne', sans-serif;
  }

  body {
    background: var(--navy);
    color: var(--text);
    font-family: var(--sans);
    min-height: 100vh;
    padding: 0;
    line-height: 1.6;
  }

  /* HERO */
  .hero {
    background: linear-gradient(135deg, #0d1b2a 0%, #162032 50%, #0d1b2a 100%);
    border-bottom: 1px solid var(--border-bright);
    padding: 56px 48px 48px;
    position: relative;
    overflow: hidden;
  }

  .hero::before {
    content: '';
    position: absolute;
    top: -80px; right: -80px;
    width: 400px; height: 400px;
    background: radial-gradient(circle, rgba(37,99,235,0.12) 0%, transparent 70%);
    pointer-events: none;
  }

  .hero::after {
    content: '';
    position: absolute;
    bottom: -60px; left: 20%;
    width: 300px; height: 300px;
    background: radial-gradient(circle, rgba(6,182,212,0.08) 0%, transparent 70%);
    pointer-events: none;
  }

  .badge-row {
    display: flex;
    gap: 8px;
    flex-wrap: wrap;
    margin-bottom: 24px;
  }

  .badge {
    font-family: var(--mono);
    font-size: 11px;
    padding: 4px 10px;
    border-radius: 4px;
    letter-spacing: 0.05em;
    font-weight: 600;
    border: 1px solid;
  }
  .badge-blue { background: rgba(37,99,235,0.15); color: #60a5fa; border-color: rgba(37,99,235,0.3); }
  .badge-cyan { background: rgba(6,182,212,0.12); color: #22d3ee; border-color: rgba(6,182,212,0.25); }
  .badge-green { background: rgba(34,197,94,0.12); color: #4ade80; border-color: rgba(34,197,94,0.25); }
  .badge-amber { background: rgba(245,158,11,0.12); color: #fbbf24; border-color: rgba(245,158,11,0.25); }

  .hero-title {
    font-size: clamp(26px, 4vw, 38px);
    font-weight: 800;
    line-height: 1.15;
    letter-spacing: -0.02em;
    margin-bottom: 8px;
  }

  .hero-title span { color: var(--cyan); }

  .hero-sub {
    font-size: 15px;
    color: var(--text-dim);
    margin-bottom: 32px;
    font-weight: 400;
  }

  .meta-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
    gap: 12px;
  }

  .meta-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 14px 16px;
  }

  .meta-label {
    font-family: var(--mono);
    font-size: 10px;
    color: var(--text-muted);
    letter-spacing: 0.1em;
    text-transform: uppercase;
    margin-bottom: 4px;
  }

  .meta-value {
    font-size: 14px;
    font-weight: 600;
    color: var(--text);
  }

  /* MAIN CONTENT */
  .content {
    max-width: 900px;
    margin: 0 auto;
    padding: 48px;
  }

  section { margin-bottom: 48px; }

  .section-header {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 20px;
  }

  .section-num {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--cyan);
    background: rgba(6,182,212,0.1);
    border: 1px solid rgba(6,182,212,0.2);
    border-radius: 4px;
    padding: 3px 8px;
    letter-spacing: 0.05em;
  }

  .section-title {
    font-size: 18px;
    font-weight: 700;
    letter-spacing: -0.01em;
  }

  /* TEAM TABLE */
  .team-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 14px;
  }

  .member-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 18px;
    transition: background 0.2s, border-color 0.2s;
  }

  .member-card:hover { background: var(--card-hover); border-color: var(--border-bright); }

  .member-avatar {
    width: 40px; height: 40px;
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-family: var(--mono);
    font-size: 13px;
    font-weight: 600;
    margin-bottom: 12px;
  }

  .av-blue { background: rgba(37,99,235,0.2); color: #60a5fa; border: 1px solid rgba(37,99,235,0.3); }
  .av-cyan { background: rgba(6,182,212,0.15); color: #22d3ee; border: 1px solid rgba(6,182,212,0.25); }
  .av-green { background: rgba(34,197,94,0.15); color: #4ade80; border: 1px solid rgba(34,197,94,0.25); }

  .member-name { font-size: 14px; font-weight: 700; margin-bottom: 2px; }
  .member-id { font-family: var(--mono); font-size: 11px; color: var(--cyan); margin-bottom: 8px; }
  .member-role { font-size: 12px; color: var(--text-dim); line-height: 1.4; }

  /* WEEK TABLE */
  .week-table { width: 100%; border-collapse: collapse; }
  .week-table th {
    font-family: var(--mono);
    font-size: 11px;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    color: var(--text-muted);
    padding: 10px 14px;
    text-align: left;
    border-bottom: 1px solid var(--border-bright);
  }

  .week-table td {
    padding: 12px 14px;
    font-size: 13px;
    color: var(--text-dim);
    border-bottom: 1px solid var(--border);
    vertical-align: top;
    line-height: 1.5;
  }

  .week-table tr:last-child td { border-bottom: none; }
  .week-table tr:hover td { background: var(--card); }

  .week-num {
    font-family: var(--mono);
    font-weight: 600;
    font-size: 12px;
    color: var(--cyan);
    white-space: nowrap;
  }

  /* PROGRESS */
  .progress-list { display: flex; flex-direction: column; gap: 10px; }

  .progress-item {
    display: flex;
    align-items: center;
    gap: 14px;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 14px 16px;
  }

  .progress-item.done { border-color: rgba(34,197,94,0.2); background: rgba(34,197,94,0.04); }

  .progress-dot {
    width: 10px; height: 10px;
    border-radius: 50%;
    flex-shrink: 0;
  }
  .dot-done { background: var(--green); box-shadow: 0 0 8px rgba(34,197,94,0.4); }
  .dot-pending { background: var(--border-bright); }

  .progress-week {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--text-muted);
    min-width: 56px;
  }

  .progress-text { font-size: 13px; flex: 1; }
  .progress-text.done-text { color: var(--text); }
  .progress-text.pending-text { color: var(--text-dim); }

  .pts-badge {
    font-family: var(--mono);
    font-size: 11px;
    padding: 3px 8px;
    border-radius: 4px;
    font-weight: 600;
  }
  .pts-done { background: rgba(34,197,94,0.12); color: #4ade80; border: 1px solid rgba(34,197,94,0.2); }
  .pts-pending { background: var(--card); color: var(--text-muted); border: 1px solid var(--border); }

  /* REPO STRUCTURE */
  .folder-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 10px;
  }

  .folder-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 14px 16px;
    display: flex;
    align-items: flex-start;
    gap: 12px;
  }

  .folder-icon {
    font-size: 20px;
    margin-top: 1px;
  }

  .folder-path {
    font-family: var(--mono);
    font-size: 13px;
    color: var(--cyan);
    margin-bottom: 3px;
  }

  .folder-desc { font-size: 12px; color: var(--text-dim); }

  /* FOOTER */
  footer {
    border-top: 1px solid var(--border);
    padding: 28px 48px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 12px;
  }

  .footer-left {
    font-family: var(--mono);
    font-size: 12px;
    color: var(--text-muted);
  }

  .footer-right {
    font-size: 12px;
    color: var(--text-muted);
  }

  @media (max-width: 640px) {
    .hero { padding: 32px 24px; }
    .content { padding: 32px 24px; }
    .team-grid { grid-template-columns: 1fr; }
    .folder-grid { grid-template-columns: 1fr; }
    footer { padding: 24px; }
  }
</style>
</head>
<body>

<div class="hero">
  <div class="badge-row">
    <span class="badge badge-blue">CN-LAB</span>
    <span class="badge badge-cyan">SECTION V-4</span>
    <span class="badge badge-amber">PROBLEM 1</span>
    <span class="badge badge-green">CCP-CNS2026</span>
  </div>

  <h1 class="hero-title">Multi-Site <span>Enterprise</span><br>Network</h1>
  <p class="hero-sub">Complex Computing Problem · Computer Networks Lab · Muhammad Fahad Irshad</p>

  <div class="meta-grid">
    <div class="meta-card">
      <div class="meta-label">Organization</div>
      <div class="meta-value">Apex Manufacturing</div>
    </div>
    <div class="meta-card">
      <div class="meta-label">Duration</div>
      <div class="meta-value">5 Weeks</div>
    </div>
    <div class="meta-card">
      <div class="meta-label">Tools</div>
      <div class="meta-value">GNS3 · Wireshark · Kali</div>
    </div>
    <div class="meta-card">
      <div class="meta-label">Submission</div>
      <div class="meta-value">GitHub + LMS</div>
    </div>
  </div>
</div>

<div class="content">

  <!-- TEAM -->
  <section>
    <div class="section-header">
      <span class="section-num">01</span>
      <h2 class="section-title">Team Members</h2>
    </div>
    <div class="team-grid">
      <div class="member-card">
        <div class="member-avatar av-blue">FA</div>
        <div class="member-name">Faizan Amir</div>
        <div class="member-id">F20242661216</div>
        <div class="member-role">Network Architect + Testing & QA</div>
      </div>
      <div class="member-card">
        <div class="member-avatar av-cyan">HJ</div>
        <div class="member-name">Hamna Jabbar</div>
        <div class="member-id">F2024266770</div>
        <div class="member-role">Security Engineer + Automation Lead</div>
      </div>
      <div class="member-card">
        <div class="member-avatar av-green">MA</div>
        <div class="member-name">Meesam Ali</div>
        <div class="member-id">F2024266280</div>
        <div class="member-role">Documentation Lead + Project Manager</div>
      </div>
    </div>
  </section>

  <!-- PROBLEM -->
  <section>
    <div class="section-header">
      <span class="section-num">02</span>
      <h2 class="section-title">Problem Summary</h2>
    </div>
    <div style="background: var(--card); border: 1px solid var(--border); border-radius: 10px; padding: 20px 22px; font-size: 14px; color: var(--text-dim); line-height: 1.75; border-left: 3px solid var(--cyan);">
      Apex Manufacturing operates from a single HQ with three departments — Sales (VLAN 10), Engineering (VLAN 20), and Admin (VLAN 30). The company suspects unauthorized access attempts. We design and implement a secured, VLAN-segmented enterprise network in GNS3, configure inter-VLAN routing via router-on-a-stick, enforce DHCP and ACL policies, deploy an Ubuntu web server in the Admin VLAN, simulate a DoS attack from Kali Linux, capture and analyze traffic in Wireshark, and demonstrate live mitigation through targeted ACL updates.
    </div>
  </section>

  <!-- PROGRESS -->
  <section>
    <div class="section-header">
      <span class="section-num">03</span>
      <h2 class="section-title">Weekly Progress</h2>
    </div>
    <div class="progress-list">
      <div class="progress-item done">
        <div class="progress-dot dot-done"></div>
        <span class="progress-week">Week 1</span>
        <span class="progress-text done-text">Team charter, topology design, IP addressing plan, GitHub setup, risk matrix</span>
        <span class="pts-badge pts-done">15 pts</span>
      </div>
      <div class="progress-item">
        <div class="progress-dot dot-pending"></div>
        <span class="progress-week">Week 2</span>
        <span class="progress-text pending-text">GNS3 implementation, VLAN config, ping matrix, SSH proof, running configs</span>
        <span class="pts-badge pts-pending">20 pts</span>
      </div>
      <div class="progress-item">
        <div class="progress-dot dot-pending"></div>
        <span class="progress-week">Week 3</span>
        <span class="progress-text pending-text">L2 security, ACLs, DoS attack simulation, PCAP capture, mitigation video</span>
        <span class="pts-badge pts-pending">25 pts</span>
      </div>
      <div class="progress-item">
        <div class="progress-dot dot-pending"></div>
        <span class="progress-week">Week 4</span>
        <span class="progress-text pending-text">NAT config, baseline performance report, final GNS3 integration, test matrix</span>
        <span class="pts-badge pts-pending">20 pts</span>
      </div>
      <div class="progress-item">
        <div class="progress-dot dot-pending"></div>
        <span class="progress-week">Week 5</span>
        <span class="progress-text pending-text">Final report (15–20 pages), demo video (8–10 min), presentation, peer evals</span>
        <span class="pts-badge pts-pending">20 pts</span>
      </div>
    </div>
  </section>

  <!-- REPO STRUCTURE -->
  <section>
    <div class="section-header">
      <span class="section-num">04</span>
      <h2 class="section-title">Repository Structure</h2>
    </div>
    <div class="folder-grid">
      <div class="folder-card">
        <div class="folder-icon">📁</div>
        <div>
          <div class="folder-path">/configs</div>
          <div class="folder-desc">Router and switch running configurations (.txt)</div>
        </div>
      </div>
      <div class="folder-card">
        <div class="folder-icon">📁</div>
        <div>
          <div class="folder-path">/diagrams</div>
          <div class="folder-desc">Network topology diagrams (draw.io / PDF)</div>
        </div>
      </div>
      <div class="folder-card">
        <div class="folder-icon">📁</div>
        <div>
          <div class="folder-path">/reports</div>
          <div class="folder-desc">Weekly status reports and final documentation</div>
        </div>
      </div>
      <div class="folder-card">
        <div class="folder-icon">📁</div>
        <div>
          <div class="folder-path">/scripts</div>
          <div class="folder-desc">Python automation and attack simulation scripts</div>
        </div>
      </div>
    </div>
  </section>

  <!-- WEEKLY BREAKDOWN -->
  <section>
    <div class="section-header">
      <span class="section-num">05</span>
      <h2 class="section-title">Role Breakdown by Week</h2>
    </div>
    <table class="week-table">
      <thead>
        <tr>
          <th>Week</th>
          <th>Faizan Amir</th>
          <th>Hamna Jabbar</th>
          <th>Meesam Ali</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td class="week-num">Week 1</td>
          <td>IP plan, topology design</td>
          <td>GitHub setup, charter</td>
          <td>Risk matrix, status report</td>
        </tr>
        <tr>
          <td class="week-num">Week 2</td>
          <td>GNS3 implementation, routing</td>
          <td>ACL, DHCP snooping, SSH</td>
          <td>Config docs, screenshots</td>
        </tr>
        <tr>
          <td class="week-num">Week 3</td>
          <td>L2 security, attack topology</td>
          <td>DoS simulation, PCAP, mitigation</td>
          <td>Attack video, weekly report</td>
        </tr>
        <tr>
          <td class="week-num">Week 4</td>
          <td>NAT config, final GNS3</td>
          <td>iPerf testing, baseline report</td>
          <td>Test matrix, config docs</td>
        </tr>
        <tr>
          <td class="week-num">Week 5</td>
          <td>Topology finalization, defense prep</td>
          <td>Incident response report</td>
          <td>Final report + video narration</td>
        </tr>
      </tbody>
    </table>
  </section>

</div>

<footer>
  <div class="footer-left">CCP-CNS2026 · Problem 1 · Section V-4</div>
  <div class="footer-right">Instructor: Muhammad Fahad Irshad</div>
</footer>

</body>
</html>
