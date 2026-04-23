<script>
  import { goto } from '$app/navigation';
</script>
<svelte:head><title>Employer Dashboard — Job Posting</title></svelte:head>

<div class="animate-in">
  <!-- Stats -->
  <div class="grid-4" style="margin-bottom:24px;">
    <div class="stat-card"><div class="stat-label">Active Posts</div><div class="stat-value">12</div><div class="stat-change stat-up">↑ 2% this week</div></div>
    <div class="stat-card"><div class="stat-label">Applicants</div><div class="stat-value">458</div><div class="stat-change stat-up">↑ 15% this month</div></div>
    <div class="stat-card"><div class="stat-label">Interviews</div><div class="stat-value">24</div><div class="stat-change stat-down">↓ 5% this week</div></div>
    <div class="stat-card"><div class="stat-label">Hired</div><div class="stat-value">8</div><div class="stat-change stat-up">↑ 12% this quarter</div></div>
  </div>

  <div class="employer-grid">
    <!-- Pipeline chart -->
    <div class="card card-pad" style="margin-bottom:20px;grid-column:1/-1;">
      <div class="section-header">
        <span class="section-title">Hiring Pipeline</span>
        <select class="form-input form-input-bare" style="width:auto;font-size:13px;padding:6px 12px;border-radius:8px;">
          <option>Last 30 days</option>
          <option>Last 90 days</option>
          <option>This year</option>
        </select>
      </div>
      <div class="pipeline-chart" style="margin-top:16px;">
        {#each [
          {label:'Sourced',h:100,color:'#E2E8F0',val:'1,240'},
          {label:'Applied',h:80,color:'#CBD5E1',val:'458'},
          {label:'Screened',h:60,color:'rgba(30,58,110,0.3)',val:'187'},
          {label:'Interview',h:40,color:'var(--navy)',val:'24'},
          {label:'Offer',h:25,color:'rgba(37,99,235,0.6)',val:'12'},
          {label:'Hired',h:15,color:'var(--success)',val:'8'},
        ] as p}
        <div class="pipeline-col">
          <div style="font-size:13px;font-weight:700;color:var(--navy);margin-bottom:6px;">{p.val}</div>
          <div class="pipeline-bar" style="height:{p.h}px;background:{p.color};"></div>
          <div class="pipeline-label">{p.label}</div>
        </div>
        {/each}
      </div>
    </div>

    <!-- Top matches -->
    <div class="card card-pad">
      <div class="section-header">
        <span class="section-title">Top Matches</span>
        <span class="section-link" onclick={() => goto('/screening')} onkeydown={() => {}} role="button" tabindex="0">View All</span>
      </div>
      {#each [
        {i:'AM',n:'Alex Morgan',r:'Senior UX Designer',m:'94%',bg:'linear-gradient(135deg,#667eea,#764ba2)'},
        {i:'SJ',n:'Sarah Jenkins',r:'Frontend Architect',m:'91%',bg:'linear-gradient(135deg,#F59E0B,#EF4444)'},
        {i:'DC',n:'David Chen',r:'Product Manager',m:'92%',bg:'linear-gradient(135deg,#10B981,#3B82F6)'},
        {i:'LK',n:'Laura Kim',r:'Data Scientist',m:'88%',bg:'linear-gradient(135deg,#8B5CF6,#EC4899)'},
      ] as m}
      <div style="display:flex;align-items:center;gap:12px;padding:12px 0;border-bottom:1px solid var(--gray-100);">
        <div class="avatar avatar-sm" style="background:{m.bg};">{m.i}</div>
        <div style="flex:1;min-width:0;">
          <div style="font-size:14px;font-weight:600;color:var(--navy);white-space:nowrap;overflow:hidden;text-overflow:ellipsis;">{m.n}</div>
          <div style="font-size:12px;color:var(--gray-400);">{m.r}</div>
        </div>
        <span style="font-size:12px;font-weight:700;color:#059669;background:#D1FAE5;padding:3px 8px;border-radius:100px;">{m.m}</span>
        <button class="btn btn-accent btn-sm" onclick={() => goto('/screening')}>Invite</button>
      </div>
      {/each}
    </div>

    <!-- Recent activity -->
    <div class="card card-pad">
      <div class="section-header">
        <span class="section-title">Recent Activity</span>
        <span class="section-link">See all</span>
      </div>
      {#each [
        {text:'New application for Senior UX Designer',time:'2 min ago',type:'app'},
        {text:'Interview scheduled with Alex Rivera',time:'1 hr ago',type:'cal'},
        {text:'Job post "Frontend Engineer" went live',time:'3 hr ago',type:'job'},
        {text:'Sarah Jenkins accepted Quick Invite',time:'Yesterday',type:'check'},
      ] as a}
      <div style="display:flex;gap:12px;padding:12px 0;border-bottom:1px solid var(--gray-100);">
        <div style="width:36px;height:36px;background:var(--gray-100);border-radius:8px;display:flex;align-items:center;justify-content:center;flex-shrink:0;">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="var(--navy)" stroke-width="2">
            {#if a.type === 'app'}<path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14 2 14 8 20 8"/>
            {:else if a.type === 'cal'}<rect x="3" y="4" width="18" height="18" rx="2" ry="2"/><line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/><line x1="3" y1="10" x2="21" y2="10"/>
            {:else if a.type === 'job'}<rect x="2" y="7" width="20" height="14" rx="2"/><path d="M16 7V5a2 2 0 0 0-2-2h-4a2 2 0 0 0-2 2v2"/>
            {:else}<polyline points="20 6 9 17 4 12"/>
            {/if}
          </svg>
        </div>
        <div style="flex:1;">
          <div style="font-size:13px;color:var(--navy);line-height:1.5;">{a.text}</div>
          <div style="font-size:12px;color:var(--gray-400);margin-top:2px;">{a.time}</div>
        </div>
      </div>
      {/each}
    </div>
  </div>
</div>

<style>
  .employer-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; }
  @media (max-width: 800px) { .employer-grid { grid-template-columns: 1fr; } }
</style>