<script>
  import { goto } from '$app/navigation';
</script>

<svelte:head><title>My Profile — Job Posting</title></svelte:head>

<!-- Hero banner -->
<div class="hero-banner animate-in">
  <div class="profile-hero-inner">
    <div class="profile-left">
      <div style="position:relative;display:inline-block;">
        <div class="avatar avatar-lg">Xian</div>
        <div class="av-badge">
          <svg width="11" height="11" viewBox="0 0 24 24" fill="none" stroke="white" stroke-width="3"><polyline points="20 6 9 17 4 12"/></svg>
        </div>
      </div>
      <div class="profile-info">
        <h1 class="profile-name">Xian Lopez</h1>
        <div class="verified-pill">
          <svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3"><polyline points="20 6 9 17 4 12"/></svg>
          Verified Alumnus · Class of 2022
        </div>
        <div style="display:flex;gap:8px;margin-top:12px;flex-wrap:wrap;">
          <span class="tag" style="background:rgba(255,255,255,0.15);color:rgba(255,255,255,0.9);">Computer Science</span>
          <span class="tag" style="background:rgba(255,255,255,0.15);color:rgba(255,255,255,0.9);">Ateneo de Davao University</span>
        </div>
      </div>
    </div>
    <div class="profile-actions">
      <button class="btn btn-outline" style="background:rgba(255,255,255,0.1);color:white;border-color:rgba(255,255,255,0.2);" onclick={() => goto('/application')}>
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14 2 14 8 20 8"/></svg>
        Generate CV
      </button>
      <button class="btn btn-primary" style="background:rgba(255,255,255,0.2);" onclick={() => goto('/vault')}>
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="11" width="18" height="11" rx="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/></svg>
        View Vault
      </button>
    </div>
  </div>
</div>

<!-- Stats row -->
<div class="grid-4 animate-in" style="margin-bottom:28px;animation-delay:0.05s;">
  <div class="stat-card">
    <div class="stat-label">GPA</div>
    <div class="stat-value">3.9</div>
    <div class="stat-change stat-up">Top 5% of class</div>
  </div>
  <div class="stat-card">
    <div class="stat-label">Certificates</div>
    <div class="stat-value">12</div>
    <div class="stat-change stat-up">↑ 3 this year</div>
  </div>
  <div class="stat-card">
    <div class="stat-label">Honors</div>
    <div class="stat-value">5</div>
    <div class="stat-change" style="color:var(--accent);">Dean's List ×6</div>
  </div>
  <div class="stat-card">
    <div class="stat-label">Match Score</div>
    <div class="stat-value">88%</div>
    <div class="stat-change stat-up">↑ Job readiness</div>
  </div>
</div>

<!-- Main grid -->
<div class="profile-grid animate-in" style="animation-delay:0.1s;">
  <!-- Left col -->
  <div class="profile-col-main">
    <!-- Academic Honors -->
    <div class="card card-pad" style="margin-bottom:20px;">
      <div class="section-header">
        <span class="section-title">Academic Honors</span>
        <span class="section-link">View All</span>
      </div>
      {#each [
        {icon:'medal',title:"Dean's List",sub:'Awarded for 6 consecutive semesters',color:'linear-gradient(135deg,#F59E0B,#EF4444)'},
        {icon:'star',title:'Summa Cum Laude',sub:'Top 1% of the graduating class',color:'linear-gradient(135deg,#3B82F6,#8B5CF6)'},
        {icon:'award',title:'Best Thesis Award',sub:'Outstanding research in AI & ML',color:'linear-gradient(135deg,#10B981,#059669)'},
      ] as h}
      <div class="honor-row">
        <div class="honor-icon" style="background:{h.color};">
          <svg viewBox="0 0 24 24" fill="none" stroke="white" stroke-width="2" width="20" height="20">
            {#if h.icon === 'medal'}
              <circle cx="12" cy="8" r="6"/><path d="M15.477 12.89L17 22l-5-3-5 3 1.523-9.11"/>
            {:else if h.icon === 'star'}
              <polygon points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2"/>
            {:else}
              <circle cx="12" cy="8" r="6"/><path d="M15.477 12.89L17 22l-5-3-5 3 1.523-9.11"/>
            {/if}
          </svg>
        </div>
        <div style="flex:1;">
          <div style="font-size:15px;font-weight:600;color:var(--navy);">{h.title}</div>
          <div style="font-size:13px;color:var(--gray-400);margin-top:2px;">{h.sub}</div>
        </div>
        <span class="tag tag-success">Verified</span>
      </div>
      {/each}
    </div>

    <!-- Professional Experience -->
    <div class="card card-pad">
      <div class="section-header">
        <span class="section-title">Experience</span>
        <span class="section-link">Edit</span>
      </div>
      {#each [
        {role:'Product Design Intern',co:'TechCorp Inc.',period:'Jun 2023 – Aug 2023'},
        {role:'Research Assistant',co:'Ateneo de Davao University',period:'Jan 2022 – May 2023'},
      ] as exp}
      <div style="display:flex;gap:14px;margin-bottom:16px;padding-bottom:16px;border-bottom:1px solid var(--gray-100);">
        <div class="company-logo" style="background:var(--navy-mid);">{exp.co.slice(0,2).toUpperCase()}</div>
        <div>
          <div style="font-size:15px;font-weight:600;color:var(--navy);">{exp.role}</div>
          <div style="font-size:13px;color:var(--gray-400);">{exp.co}</div>
          <div style="font-size:12px;color:var(--gray-400);margin-top:2px;">{exp.period}</div>
        </div>
      </div>
      {/each}
    </div>
  </div>

  <!-- Right col -->
  <div class="profile-col-side">
    <!-- Skills -->
    <div class="card card-pad" style="margin-bottom:20px;">
      <div class="section-header">
        <span class="section-title">Professional Skills</span>
        <span class="section-link">Edit</span>
      </div>
      <div style="display:flex;flex-wrap:wrap;gap:8px;">
        {#each ['Product Strategy','Data Analysis','SQL','Python','Project Management','UX Research','Machine Learning','Figma','React','TypeScript'] as skill}
          <span class="tag">{skill}</span>
        {/each}
        <span class="tag tag-accent" style="cursor:pointer;">+ Add</span>
      </div>
    </div>

    <!-- Certifications -->
    <div class="card card-pad" style="margin-bottom:20px;">
      <div class="section-header">
        <span class="section-title">Certifications</span>
        <span class="section-link">View All</span>
      </div>
      {#each [
        {name:'AWS Cloud Practitioner',issuer:'Amazon Web Services',year:'2023'},
        {name:'Google Data Analytics',issuer:'Google',year:'2022'},
        {name:'Scrum Master (PSM I)',issuer:'Scrum.org',year:'2023'},
      ] as cert}
      <div style="display:flex;align-items:center;gap:12px;margin-bottom:12px;">
        <div style="width:36px;height:36px;background:rgba(245,158,11,0.1);border-radius:8px;display:flex;align-items:center;justify-content:center;flex-shrink:0;">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="#D97706" stroke-width="2"><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/></svg>
        </div>
        <div style="flex:1;min-width:0;">
          <div style="font-size:13px;font-weight:600;color:var(--navy);white-space:nowrap;overflow:hidden;text-overflow:ellipsis;">{cert.name}</div>
          <div style="font-size:12px;color:var(--gray-400);">{cert.issuer} · {cert.year}</div>
        </div>
      </div>
      {/each}
    </div>

    <!-- Quick actions -->
    <div class="card card-pad">
      <div class="section-title" style="margin-bottom:14px;">Quick Actions</div>
      <div style="display:flex;flex-direction:column;gap:10px;">
        <button class="btn btn-primary btn-full" onclick={() => goto('/jobs')}>
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="11" cy="11" r="8"/><line x1="21" y1="21" x2="16.65" y2="16.65"/></svg>
          Browse Jobs
        </button>
        <button class="btn btn-outline btn-full" onclick={() => goto('/vault')}>
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="11" width="18" height="11" rx="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/></svg>
          Open Vault
        </button>
        <button class="btn btn-outline btn-full" onclick={() => goto('/status')}>
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/></svg>
          Track Applications
        </button>
      </div>
    </div>
  </div>
</div>

<style>
  .profile-hero-inner {
    position: relative;
    z-index: 1;
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 24px;
    flex-wrap: wrap;
  }

  .profile-left { display: flex; align-items: center; gap: 24px; }
  .profile-info { color: white; }
  .profile-name { font-size: 26px; font-weight: 700; color: white; margin-bottom: 8px; }
  .profile-actions { display: flex; gap: 12px; flex-shrink: 0; flex-wrap: wrap; }

  .av-badge {
    position: absolute;
    bottom: 2px;
    right: 2px;
    width: 24px;
    height: 24px;
    background: #10B981;
    border-radius: 50%;
    border: 3px solid transparent;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .honor-row {
    display: flex;
    align-items: center;
    gap: 14px;
    padding: 14px 0;
    border-bottom: 1px solid var(--gray-100);
  }
  .honor-row:last-child { border-bottom: none; padding-bottom: 0; }
  .honor-icon { width: 44px; height: 44px; border-radius: 50%; display: flex; align-items: center; justify-content: center; flex-shrink: 0; }

  .profile-grid {
    display: grid;
    grid-template-columns: 1fr 360px;
    gap: 20px;
  }

  @media (max-width: 1100px) {
    .profile-grid { grid-template-columns: 1fr; }
    .profile-col-side { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; }
    .profile-col-side > .card:last-child { grid-column: 1 / -1; }
  }

  @media (max-width: 700px) {
    .profile-left { flex-direction: column; align-items: flex-start; }
    .profile-actions { width: 100%; }
    .profile-col-side { grid-template-columns: 1fr; }
    .profile-name { font-size: 20px; }
  }
</style>