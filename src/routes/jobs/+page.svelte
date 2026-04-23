<script>
  import { goto } from '$app/navigation';
  let search = '';
</script>

<svelte:head><title>Job Search — Job Posting</title></svelte:head>

<div class="jobs-layout">
  <!-- Left: Filters (desktop sidebar) -->
  <aside class="jobs-filters hide-mobile">
    <div class="card card-pad">
      <div style="font-size:15px;font-weight:700;color:var(--navy);margin-bottom:16px;">Filters</div>

      <div style="margin-bottom:20px;">
        <div style="font-size:12px;font-weight:700;color:var(--gray-400);text-transform:uppercase;letter-spacing:0.5px;margin-bottom:10px;">Degree Level</div>
        {#each ['Any','Bachelor\'s','Master\'s','PhD','Diploma'] as d}
        <label style="display:flex;align-items:center;gap:8px;padding:6px 0;cursor:pointer;font-size:14px;color:var(--gray-600);">
          <input type="radio" name="degree" style="accent-color:var(--navy);" /> {d}
        </label>
        {/each}
      </div>

      <div class="divider"></div>

      <div style="margin-bottom:20px;">
        <div style="font-size:12px;font-weight:700;color:var(--gray-400);text-transform:uppercase;letter-spacing:0.5px;margin-bottom:10px;">Job Type</div>
        {#each ['Full-time','Part-time','Contract','Internship'] as t}
        <label style="display:flex;align-items:center;gap:8px;padding:6px 0;cursor:pointer;font-size:14px;color:var(--gray-600);">
          <input type="checkbox" style="accent-color:var(--navy);" /> {t}
        </label>
        {/each}
      </div>

      <div class="divider"></div>

      <div>
        <div style="font-size:12px;font-weight:700;color:var(--gray-400);text-transform:uppercase;letter-spacing:0.5px;margin-bottom:10px;">Location</div>
        {#each ['Remote','On-site','Hybrid'] as l}
        <label style="display:flex;align-items:center;gap:8px;padding:6px 0;cursor:pointer;font-size:14px;color:var(--gray-600);">
          <input type="checkbox" style="accent-color:var(--navy);" /> {l}
        </label>
        {/each}
      </div>
    </div>
  </aside>

  <!-- Right: Job listings -->
  <div class="jobs-main">
    <!-- Search bar -->
    <div class="card card-pad" style="margin-bottom:20px;">
      <div class="input-wrap" style="margin-bottom:14px;">
        <svg class="input-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="11" cy="11" r="8"/><line x1="21" y1="21" x2="16.65" y2="16.65"/></svg>
        <input class="form-input" type="text" placeholder="Search job title, company, or keyword..." bind:value={search} />
      </div>
      <div style="display:flex;gap:8px;overflow-x:auto;padding-bottom:4px;scrollbar-width:none;">
        <button class="tag tag-accent" style="cursor:pointer;white-space:nowrap;border:1.5px solid var(--accent);">Degree ↓</button>
        <button class="tag" style="cursor:pointer;white-space:nowrap;border:1.5px solid var(--gray-200);">Skills ↓</button>
        <button class="tag" style="cursor:pointer;white-space:nowrap;border:1.5px solid var(--gray-200);">Location ↓</button>
        <button class="tag" style="cursor:pointer;white-space:nowrap;border:1.5px solid var(--gray-200);">Salary ↓</button>
        <button class="tag" style="cursor:pointer;white-space:nowrap;border:1.5px solid var(--gray-200);">Experience ↓</button>
      </div>
    </div>

    <div class="section-header">
      <span class="section-title">Hand-Picked for You</span>
      <span class="section-link">See all 48</span>
    </div>

    {#each [
      {id:1,title:'Senior Product Designer',co:'TechFlow Systems',loc:'San Francisco, CA',salary:'$140k–$180k',type:'Full-time',match:88,posted:'2 days ago',color:'#4F46E5',abbr:'TF'},
      {id:2,title:'Frontend Engineer (React)',co:'Lumina Creative',loc:'Remote',salary:'$120k–$155k',type:'Contract',match:92,posted:'5 hours ago',color:'#059669',abbr:'LC'},
      {id:3,title:'UX Research Lead',co:'Blue Knight Corp',loc:'Austin, TX',salary:'$150k–$200k',type:'Full-time',match:89,posted:'1 week ago',color:'#DC2626',abbr:'BK'},
      {id:4,title:'Data Scientist',co:'DataSync Inc',loc:'New York, NY',salary:'$130k–$165k',type:'Full-time',match:85,posted:'3 days ago',color:'#7C3AED',abbr:'DS'},
      {id:5,title:'Product Manager',co:'Horizon Tech',loc:'Seattle, WA',salary:'$160k–$190k',type:'Full-time',match:83,posted:'1 day ago',color:'#0891B2',abbr:'HT'},
      {id:6,title:'ML Engineer',co:'AI Ventures',loc:'Remote',salary:'$145k–$175k',type:'Full-time',match:80,posted:'4 days ago',color:'#7C3AED',abbr:'AI'},
    ] as job}
    <div class="job-card animate-in" style="margin-bottom:14px;animation-delay:{job.id * 0.04}s;" onclick={() => goto('/jobs/detail')} onkeydown={() => {}} role="button" tabindex="0">
      <div style="display:flex;align-items:flex-start;gap:16px;">
        <div class="company-logo" style="background:{job.color};">{job.abbr}</div>
        <div style="flex:1;min-width:0;">
          <div style="display:flex;align-items:flex-start;justify-content:space-between;gap:12px;">
            <div>
              <div style="font-size:16px;font-weight:700;color:var(--navy);margin-bottom:3px;">{job.title}</div>
              <div style="font-size:14px;color:var(--gray-400);">{job.co} · {job.loc}</div>
            </div>
            <div class="match-badge {job.match >= 87 ? 'match-high' : 'match-med'}" style="flex-shrink:0;">{job.match}%</div>
          </div>
          <div style="display:flex;flex-wrap:wrap;gap:8px;margin-top:12px;">
            <span class="tag">{job.salary}</span>
            <span class="tag">{job.type}</span>
            <span class="tag">{job.posted}</span>
          </div>
        </div>
      </div>
      <div style="display:flex;gap:10px;margin-top:16px;">
        <button class="btn btn-primary" style="flex:1;" onclick={(e) => { e.stopPropagation(); goto('/application'); }}>Apply Now</button>
        <button class="btn btn-outline" onclick={(e) => e.stopPropagation()}>
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M19 21l-7-5-7 5V5a2 2 0 0 1 2-2h10a2 2 0 0 1 2 2z"/></svg>
        </button>
      </div>
    </div>
    {/each}
  </div>
</div>

<style>
  .jobs-layout {
    display: grid;
    grid-template-columns: 260px 1fr;
    gap: 24px;
  }

  .jobs-filters { position: sticky; top: 96px; height: fit-content; }
  .jobs-main { min-width: 0; }

  @media (max-width: 900px) {
    .jobs-layout { grid-template-columns: 1fr; }
  }
</style>