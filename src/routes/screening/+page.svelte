<svelte:head><title>Applicant Screening — Job Posting</title></svelte:head>

<div class="animate-in">
  <div style="margin-bottom:20px;">
    <div style="font-size:12px;color:var(--gray-400);font-weight:600;text-transform:uppercase;letter-spacing:0.5px;margin-bottom:4px;">Active Listing</div>
    <div style="display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:12px;">
      <div>
        <h1 style="font-size:24px;font-weight:700;color:var(--navy);">Senior UX Designer</h1>
        <div style="font-size:14px;color:var(--gray-400);">24 total applicants · 8 new today</div>
      </div>
      <div style="display:flex;gap:8px;">
        <button class="btn btn-outline btn-sm">Export</button>
        <button class="btn btn-primary btn-sm">Schedule Interviews</button>
      </div>
    </div>
  </div>

  <!-- Filter tabs -->
  <div class="card card-pad" style="margin-bottom:20px;">
    <div style="display:flex;gap:8px;overflow-x:auto;scrollbar-width:none;">
      <button class="btn btn-primary btn-sm">All Applicants</button>
      <button class="btn btn-outline btn-sm">Highly Matched</button>
      <button class="btn btn-outline btn-sm">Recent</button>
      <button class="btn btn-outline btn-sm">Shortlisted</button>
      <button class="btn btn-outline btn-sm">Rejected</button>
    </div>
  </div>

  <!-- Applicant table header (desktop) -->
  <div class="card" style="margin-bottom:0;border-radius:var(--radius) var(--radius) 0 0;border-bottom:none;">
    <div class="screening-header hide-mobile">
      <span>Applicant</span>
      <span>Match</span>
      <span>Skills</span>
      <span>Applied</span>
      <span>Status</span>
      <span>Actions</span>
    </div>
  </div>

  <!-- Applicants -->
  {#each [
    {i:'AR',n:'Alex Rivera',r:'Senior Designer at TechFlow',m:96,skills:['Figma','Prototyping','Design Ops'],t:'2h ago',status:'New',bg:'linear-gradient(135deg,#667eea,#764ba2)'},
    {i:'SJ',n:'Sarah Jenkins',r:'Product Designer at CreativeCo',m:92,skills:['User Research','Adobe XD'],t:'1d ago',status:'Shortlisted',bg:'linear-gradient(135deg,#F59E0B,#EF4444)'},
    {i:'MC',n:'Marcus Chen',r:'UX Consultant (Freelance)',m:89,skills:['Strategic Design','Workshop'],t:'3d ago',status:'New',bg:'linear-gradient(135deg,#10B981,#3B82F6)'},
    {i:'LK',n:'Laura Kim',r:'UI/UX Designer at StartupXYZ',m:84,skills:['Sketch','Motion','Branding'],t:'4d ago',status:'Reviewing',bg:'linear-gradient(135deg,#8B5CF6,#EC4899)'},
    {i:'BT',n:'Ben Torres',r:'UX Lead at DesignLab',m:81,skills:['Wireframing','User Testing'],t:'5d ago',status:'New',bg:'linear-gradient(135deg,#DC2626,#F59E0B)'},
  ] as a, idx}
  <div class="card" style="border-radius:0;border-bottom:{idx < 4 ? 'none' : ''};border-top:none;">
    <!-- Desktop row -->
    <div class="screening-row hide-mobile">
      <div style="display:flex;align-items:center;gap:12px;">
        <div class="avatar avatar-sm" style="background:{a.bg};">{a.i}</div>
        <div>
          <div style="font-size:14px;font-weight:600;color:var(--navy);">{a.n}</div>
          <div style="font-size:12px;color:var(--gray-400);">{a.r}</div>
        </div>
      </div>
      <div>
        <span style="font-size:14px;font-weight:700;color:{a.m >= 90 ? '#059669' : 'var(--navy)'};">{a.m}%</span>
      </div>
      <div style="display:flex;flex-wrap:wrap;gap:4px;">
        {#each a.skills.slice(0,2) as s}
          <span class="tag" style="font-size:11px;padding:3px 8px;">{s}</span>
        {/each}
      </div>
      <div style="font-size:13px;color:var(--gray-400);">{a.t}</div>
      <div>
        <span style="font-size:12px;font-weight:700;padding:4px 10px;border-radius:100px;background:{a.status === 'Shortlisted' ? '#D1FAE5' : a.status === 'Reviewing' ? '#FEF3C7' : 'var(--gray-100)'};color:{a.status === 'Shortlisted' ? '#059669' : a.status === 'Reviewing' ? '#D97706' : 'var(--gray-600)'};">{a.status}</span>
      </div>
      <div style="display:flex;gap:6px;">
        <button class="btn btn-outline btn-sm">View</button>
        <button class="btn btn-accent btn-sm">Invite</button>
      </div>
    </div>

    <!-- Mobile card -->
    <div class="applicant-card" style="border:none;border-radius:0;">
      <div style="display:flex;align-items:flex-start;gap:12px;margin-bottom:10px;">
        <div style="position:relative;">
          <div style="position:absolute;top:-4px;left:-4px;background:var(--navy);color:white;font-size:9px;font-weight:700;padding:2px 6px;border-radius:100px;white-space:nowrap;z-index:1;">{a.m}%</div>
          <div class="avatar avatar-sm" style="background:{a.bg};width:48px;height:48px;margin-top:10px;">{a.i}</div>
        </div>
        <div style="margin-top:10px;">
          <div style="font-size:14px;font-weight:700;color:var(--navy);">{a.n}</div>
          <div style="font-size:12px;color:var(--gray-400);">{a.r}</div>
          <div style="font-size:11px;color:var(--gray-400);">Applied {a.t}</div>
        </div>
      </div>
      <div style="display:flex;flex-wrap:wrap;gap:6px;margin-bottom:12px;">
        {#each a.skills as s}<span class="tag">{s}</span>{/each}
      </div>
      <div style="display:flex;gap:8px;">
        <button class="btn btn-outline" style="flex:1;padding:10px;">View Profile →</button>
        <button class="btn btn-accent btn-sm">Invite</button>
      </div>
    </div>
  </div>
  {/each}

  <div class="card" style="border-radius:0 0 var(--radius) var(--radius);border-top:none;padding:14px 20px;display:flex;justify-content:center;">
    <button class="btn btn-outline btn-sm">Load more applicants</button>
  </div>
</div>

<style>
  .screening-header {
    display: grid;
    grid-template-columns: 2fr 80px 1.5fr 100px 100px 160px;
    gap: 12px;
    padding: 12px 20px;
    font-size: 11px;
    font-weight: 700;
    color: var(--gray-400);
    text-transform: uppercase;
    letter-spacing: 0.5px;
  }

  .screening-row {
    display: grid;
    grid-template-columns: 2fr 80px 1.5fr 100px 100px 160px;
    gap: 12px;
    padding: 16px 20px;
    align-items: center;
    transition: background 0.15s;
    cursor: pointer;
  }
  .screening-row:hover { background: var(--gray-50); }

  /* Show mobile cards, hide desktop row on mobile */
  @media (min-width: 901px) {
    .applicant-card { display: none !important; }
  }
  @media (max-width: 900px) {
    .screening-row { display: none !important; }
    .screening-header { display: none !important; }
  }
</style>