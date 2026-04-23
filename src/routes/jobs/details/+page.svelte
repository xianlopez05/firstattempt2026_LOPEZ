<script>
  import { goto } from '$app/navigation';
</script>
<svelte:head><title>Job Details — Job Posting</title></svelte:head>

<div class="detail-layout animate-in">
  <div class="detail-main">
    <!-- Job header -->
    <div class="card card-pad" style="margin-bottom:20px;">
      <div style="display:flex;align-items:flex-start;gap:16px;margin-bottom:20px;">
        <div class="company-logo" style="background:#4F46E5;width:60px;height:60px;font-size:16px;border-radius:14px;flex-shrink:0;">TF</div>
        <div style="flex:1;">
          <h1 style="font-size:24px;font-weight:700;color:var(--navy);margin-bottom:4px;">Senior Product Designer</h1>
          <div style="font-size:15px;color:var(--gray-400);margin-bottom:12px;">TechFlow, Inc. · San Francisco, CA</div>
          <div style="display:flex;flex-wrap:wrap;gap:8px;">
            <span class="tag">$140k–$180k</span>
            <span class="tag">Full-time</span>
            <span class="tag tag-success">Posted 2 days ago</span>
            <span class="tag">142 applicants</span>
          </div>
        </div>
      </div>
      <div style="display:flex;gap:12px;flex-wrap:wrap;">
        <button class="btn btn-primary btn-lg" style="flex:1;min-width:200px;" onclick={() => goto('/application')}>
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="2" y="3" width="20" height="14" rx="2"/><path d="M8 21h8M12 17v4"/></svg>
          Apply with Job Posting
        </button>
        <button class="btn btn-outline">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M19 21l-7-5-7 5V5a2 2 0 0 1 2-2h10a2 2 0 0 1 2 2z"/></svg>
          Save
        </button>
        <button class="btn btn-outline">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="18" cy="5" r="3"/><circle cx="6" cy="12" r="3"/><circle cx="18" cy="19" r="3"/><line x1="8.59" y1="13.51" x2="15.42" y2="17.49"/></svg>
          Share
        </button>
      </div>
    </div>

    <!-- Match score -->
    <div class="card card-pad" style="background:linear-gradient(135deg,var(--navy) 0%,var(--navy-mid) 100%);border:none;margin-bottom:20px;">
      <div style="display:flex;align-items:center;justify-content:space-between;gap:24px;flex-wrap:wrap;">
        <div>
          <div style="font-size:12px;font-weight:700;color:rgba(255,255,255,0.5);text-transform:uppercase;letter-spacing:0.5px;margin-bottom:6px;">Passport Match Score</div>
          <div style="font-size:16px;color:rgba(255,255,255,0.8);">Based on your verified skills and experience</div>
          <div style="margin-top:14px;">
            <div style="height:8px;background:rgba(255,255,255,0.15);border-radius:100px;width:300px;max-width:100%;overflow:hidden;">
              <div style="height:100%;width:85%;background:#10B981;border-radius:100px;"></div>
            </div>
          </div>
        </div>
        <div style="text-align:center;">
          <div style="font-size:52px;font-weight:800;color:white;line-height:1;">85%</div>
          <div style="font-size:13px;color:rgba(255,255,255,0.5);margin-top:4px;">Match Score</div>
        </div>
      </div>
    </div>

    <!-- Skill match -->
    <div class="card card-pad" style="margin-bottom:20px;">
      <div style="font-size:17px;font-weight:700;color:var(--navy);margin-bottom:16px;">Skill Match Analysis</div>
      <div style="margin-bottom:16px;">
        <div style="font-size:12px;font-weight:700;color:var(--gray-400);text-transform:uppercase;letter-spacing:0.5px;margin-bottom:10px;">✓ Matched Skills (6)</div>
        <div style="display:flex;flex-wrap:wrap;gap:8px;">
          {#each ['React Basics','Motion Design','Figma','UX Research','Prototyping','Design Systems'] as s}
            <span class="tag tag-success">✓ {s}</span>
          {/each}
        </div>
      </div>
      <div class="divider"></div>
      <div>
        <div style="font-size:12px;font-weight:700;color:var(--gray-400);text-transform:uppercase;letter-spacing:0.5px;margin-bottom:10px;">⚠ Potential Gaps (2)</div>
        <div style="display:flex;flex-wrap:wrap;gap:8px;">
          <span class="tag tag-warning">Advanced Animation</span>
          <span class="tag tag-warning">Video Editing</span>
        </div>
      </div>
    </div>

    <!-- About the role -->
    <div class="card card-pad" style="margin-bottom:20px;">
      <div style="font-size:17px;font-weight:700;color:var(--navy);margin-bottom:14px;">About the Role</div>
      <p style="font-size:15px;color:var(--gray-600);line-height:1.8;margin-bottom:14px;">We are looking for a Senior Product Designer to join our core product team. You will be responsible for leading the design of new features from concept to execution, working closely with engineering and product management.</p>
      <ul style="font-size:15px;color:var(--gray-600);line-height:1.8;padding-left:20px;display:flex;flex-direction:column;gap:6px;">
        <li>Drive the design vision for our flagship platform.</li>
        <li>Collaborate with cross-functional teams to define requirements.</li>
        <li>Create high-fidelity prototypes and design specifications.</li>
        <li>Mentor junior designers and contribute to our design system.</li>
      </ul>
    </div>
  </div>

  <!-- Side panel -->
  <aside class="detail-side">
    <div class="card card-pad" style="margin-bottom:16px;">
      <div style="font-size:15px;font-weight:700;color:var(--navy);margin-bottom:14px;">Job Details</div>
      {#each [
        {label:'Location',value:'San Francisco, CA'},
        {label:'Employment Type',value:'Full-time'},
        {label:'Salary Range',value:'$140k – $180k'},
        {label:'Experience',value:'5+ years'},
        {label:'Department',value:'Product Design'},
      ] as d}
      <div style="display:flex;justify-content:space-between;padding:10px 0;border-bottom:1px solid var(--gray-100);font-size:14px;">
        <span style="color:var(--gray-400);">{d.label}</span>
        <span style="font-weight:600;color:var(--navy);">{d.value}</span>
      </div>
      {/each}
    </div>

    <div class="card card-pad">
      <div style="font-size:15px;font-weight:700;color:var(--navy);margin-bottom:14px;">About TechFlow</div>
      <div class="company-logo" style="background:#4F46E5;width:52px;height:52px;margin-bottom:12px;border-radius:12px;">TF</div>
      <p style="font-size:14px;color:var(--gray-600);line-height:1.7;">TechFlow Systems is a leading product design and engineering company based in San Francisco with over 500 employees.</p>
      <div style="margin-top:12px;display:flex;flex-direction:column;gap:6px;font-size:13px;color:var(--gray-400);">
        <div>🏢 500–1,000 employees</div>
        <div>💼 Technology · SaaS</div>
        <div>📍 San Francisco, CA</div>
      </div>
    </div>
  </aside>
</div>

<style>
  .detail-layout {
    display: grid;
    grid-template-columns: 1fr 320px;
    gap: 24px;
    align-items: start;
  }
  @media (max-width: 1000px) {
    .detail-layout { grid-template-columns: 1fr; }
    .detail-side { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; }
  }
  @media (max-width: 600px) {
    .detail-side { grid-template-columns: 1fr; }
  }
</style>