              HTML


<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Assignment 8.1 — Dashboard Grid Layout</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

  <!-- Step 4 & 5: Outer Grid Container -->
  <div class="dashboard-layout">

    <!-- Step 1: Dashboard Header -->
    <header class="dashboard-header">
      <div class="header-brand">Analytics<span>Hub</span></div>
      <div class="header-profile">
        <span class="user-role">Administrator</span>
        <div class="avatar">JD</div>
      </div>
    </header>

    <!-- Step 2: Sidebar -->
    <aside class="dashboard-sidebar">
      <nav class="sidebar-nav">
        <a href="#overview" class="active">📊 Overview</a>
        <a href="#analytics">📈 Analytics</a>
        <a href="#orders">📦 Orders</a>
        <a href="#customers">👥 Customers</a>
        <a href="#settings">⚙️ Settings</a>
      </nav>
    </aside>

    <!-- Step 2: Main Content Area -->
    <main class="dashboard-main">
      <div class="main-intro">
        <h1>Dashboard Overview</h1>
        <p>Live metrics and system activity for the current billing cycle.</p>
      </div>

      <!-- Step 3 & 6: 4 Stat Cards in an Internal Grid Container with Gap -->
      <section class="stats-grid">
        
        <!-- Card 1 -->
        <article class="stat-card">
          <div class="stat-head">
            <span class="stat-label">Total Revenue</span>
            <span class="stat-badge positive">+14.2%</span>
          </div>
          <div class="stat-value">$48,250</div>
          <p class="stat-meta">Compared to $42,100 last month</p>
        </article>

        <!-- Card 2 -->
        <article class="stat-card">
          <div class="stat-head">
            <span class="stat-label">Active Subscriptions</span>
            <span class="stat-badge positive">+8.1%</span>
          </div>
          <div class="stat-value">1,420</div>
          <p class="stat-meta">114 new signups this week</p>
        </article>

        <!-- Card 3 -->
        <article class="stat-card">
          <div class="stat-head">
            <span class="stat-label">Conversion Rate</span>
            <span class="stat-badge negative">-0.4%</span>
          </div>
          <div class="stat-value">3.24%</div>
          <p class="stat-meta">Down from 3.64% previous cycle</p>
        </article>

        <!-- Card 4 -->
        <article class="stat-card">
          <div class="stat-head">
            <span class="stat-label">Avg. Response Time</span>
            <span class="stat-badge positive">-18ms</span>
          </div>
          <div class="stat-value">142ms</div>
          <p class="stat-meta">Global CDN edge average</p>
        </article>

      </section>

      <!-- Placeholder Content Area to Illustrate Dashboard Layout -->
      <section class="content-panel">
        <h2>Recent Activity</h2>
        <p>Your server clusters are healthy and processing events normally.</p>
      </section>
    </main>

  </div>

</body>
</html>




                CSS


/* --- Global Reset & Design Tokens --- */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

:root {
  --primary: #2563eb;
  --bg-dark: #0f172a;
  --bg-sidebar: #1e293b;
  --bg-main: #f8fafc;
  --bg-card: #ffffff;
  --border: #e2e8f0;
  --text-main: #0f172a;
  --text-muted: #64748b;
  --success: #16a34a;
  --danger: #dc2626;
}

body {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  color: var(--text-main);
  background-color: var(--bg-main);
  min-height: 100vh;
}

/* ================= STEPS 4 & 5: OUTER GRID LAYOUT ================= */
.dashboard-layout {
  display: grid;
  /* 
    Column 1: Fixed 240px Sidebar
    Column 2: 1fr takes the rest of the available viewport width
  */
  grid-template-columns: 240px 1fr;
  /* 
    Row 1: Fixed 64px Header
    Row 2: 1fr expands down to take the full viewport height
  */
  grid-template-rows: 64px 1fr;
  min-height: 100vh;
}

/* ================= STEP 1: HEADER ================= */
.dashboard-header {
  /* Spans across both columns on row 1 */
  grid-column: 1 / -1;
  background-color: #ffffff;
  border-bottom: 1px solid var(--border);
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 1.5rem;
}

.header-brand {
  font-size: 1.25rem;
  font-weight: 800;
  color: var(--bg-dark);
}

.header-brand span {
  color: var(--primary);
}

.header-profile {
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.user-role {
  font-size: 0.85rem;
  color: var(--text-muted);
}

.avatar {
  width: 36px;
  height: 36px;
  border-radius: 50%;
  background-color: var(--primary);
  color: #ffffff;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.85rem;
  font-weight: 700;
}

/* ================= STEP 2: SIDEBAR ================= */
.dashboard-sidebar {
  background-color: var(--bg-sidebar);
  border-right: 1px solid #334155;
  padding: 1.5rem 1rem;
}

.sidebar-nav {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.sidebar-nav a {
  display: block;
  text-decoration: none;
  color: #94a3b8;
  padding: 0.75rem 1rem;
  border-radius: 8px;
  font-size: 0.95rem;
  font-weight: 500;
  transition: all 0.2s ease;
}

.sidebar-nav a:hover {
  background-color: #334155;
  color: #ffffff;
}

.sidebar-nav a.active {
  background-color: var(--primary);
  color: #ffffff;
}

/* ================= STEP 2: MAIN CONTENT AREA ================= */
.dashboard-main {
  padding: 2rem;
  display: flex;
  flex-direction: column;
  gap: 2rem;
  overflow-y: auto;
}

.main-intro h1 {
  font-size: 1.75rem;
  font-weight: 800;
  color: var(--text-main);
}

.main-intro p {
  color: var(--text-muted);
  margin-top: 0.25rem;
  font-size: 0.95rem;
}

/* ================= STEPS 3 & 6: STATS CARDS GRID ================= */
.stats-grid {
  display: grid;
  /* Automatically fits 4 columns on large screens, wraps into fewer columns smoothly */
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 1.5rem;                        /* Step 6: Gap between cards */
}

.stat-card {
  background-color: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: 10px;
  padding: 1.25rem 1.5rem;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.04);
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.stat-head {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.stat-label {
  font-size: 0.85rem;
  font-weight: 600;
  color: var(--text-muted);
}

.stat-badge {
  font-size: 0.75rem;
  font-weight: 700;
  padding: 0.2rem 0.5rem;
  border-radius: 4px;
}

.stat-badge.positive {
  background-color: #dcfce7;
  color: var(--success);
}

.stat-badge.negative {
  background-color: #fee2e2;
  color: var(--danger);
}

.stat-value {
  font-size: 2rem;
  font-weight: 800;
  color: var(--text-main);
  letter-spacing: -0.02em;
}

.stat-meta {
  font-size: 0.8rem;
  color: var(--text-muted);
}

/* Extra content panel placeholder */
.content-panel {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: 10px;
  padding: 1.5rem;
}

.content-panel h2 {
  font-size: 1.15rem;
  margin-bottom: 0.5rem;
}

.content-panel p {
  color: var(--text-muted);
  font-size: 0.9rem;
}

/* ================= RESPONSIVE BEHAVIOR ================= */
@media (max-width: 768px) {
  .dashboard-layout {
    grid-template-columns: 1fr;       /* Collapse sidebar into single stacked column */
    grid-template-rows: auto auto 1fr;
  }

  .dashboard-sidebar {
    padding: 0.75rem;
  }

  .sidebar-nav {
    flex-direction: row;
    overflow-x: auto;
  }

  .dashboard-main {
    padding: 1.25rem;
  }
}