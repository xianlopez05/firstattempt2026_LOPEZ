<script>
  import { goto } from '$app/navigation';
</script>
<svelte:head><title>Instant Application — Job Posting</title></svelte:head>

<div class="app-layout animate-in">
  <div class="app-main">
    <div class="card card-pad" style="margin-bottom:20px;">
      <div style="display:flex;align-items:center;gap:16px;margin-bottom:20px;padding-bottom:20px;border-bottom:1px solid var(--gray-100);">
        <div class="avatar avatar-lg">AK</div>
        <div>
          <h2 style="font-size:20px;font-weight:700;color:var(--navy);margin-bottom:4px;">Alex Knight</h2>
          <div class="verified-pill" style="margin-bottom:6px;">✓ Verified Student</div>
          <div style="font-size:14px;color:var(--gray-400);">Master of Computer Science</div>
        </div>
      </div>

      <div style="background:rgba(37,99,235,0.05);border:1px solid rgba(37,99,235,0.2);border-radius:12px;padding:16px;margin-bottom:20px;">
        <div style="font-size:14px;font-weight:700;color:var(--navy);margin-bottom:4px;">Ateneo de Davao University Verification</div>
        <div style="font-size:13px;color:var(--gray-400);margin-bottom:8px;">This profile has been officially verified by the university registrar's office for the 2023-2024 academic year.</div>
        <span class="section-link">View Credentials →</span>
      </div>

      <div style="font-size:16px;font-weight:700;color:var(--navy);margin-bottom:14px;">Academic Records</div>
      {#each [
        {name:'Official Transcript.pdf',date:'Updated Jul 15, 2023'},
        {name:'Bachelor Degree Certificate.pdf',date:'Updated Jun 05, 2023'},
        {name:'Awards & Honors.pdf',date:'Updated Sep 01, 2023'},
      ] as r}
      <div class="record-row">
        <div class="record-icon">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="#2563EB" stroke-width="2"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14 2 14 8 20 8"/></svg>
        </div>
        <div style="flex:1;min-width:0;">
          <div style="font-size:14px;font-weight:600;color:var(--navy);white-space:nowrap;overflow:hidden;text-overflow:ellipsis;">{r.name}</div>
          <div style="font-size:12px;color:var(--gray-400);">{r.date}</div>
        </div>
        <button class="icon-btn">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="7 10 12 15 17 10"/><line x1="12" y1="15" x2="12" y2="3"/></svg>
        </button>
      </div>
      {/each}
    </div>

    <div class="card card-pad" style="margin-bottom:20px;">
      <div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:12px;">
        <div style="font-size:16px;font-weight:700;color:var(--navy);">Cover Letter</div>
        <button class="btn btn-outline btn-sm">Edit ✏</button>
      </div>
      <div class="message-bubble">Dear Hiring Committee, I am writing to express my strong interest in the Research Assistant position. My Master's in Computer Science has provided me with a deep foundation in algorithm design and machine learning, which I am eager to apply to your current projects. I have previously worked on several collaborative academic papers and value the rigor of university research...</div>
    </div>
  </div>

  <aside class="app-side">
    <div class="card card-pad" style="margin-bottom:16px;">
      <div style="font-size:15px;font-weight:700;color:var(--navy);margin-bottom:14px;">Applying For</div>
      <div style="display:flex;gap:12px;margin-bottom:14px;">
        <div class="company-logo" style="background:#4F46E5;">TF</div>
        <div>
          <div style="font-size:14px;font-weight:600;color:var(--navy);">Senior Product Designer</div>
          <div style="font-size:13px;color:var(--gray-400);">TechFlow, Inc.</div>
        </div>
      </div>
      <div class="divider"></div>
      <div style="display:flex;justify-content:space-between;font-size:13px;margin-bottom:8px;">
        <span style="color:var(--gray-400);">Match Score</span>
        <span style="font-weight:700;color:#059669;">85%</span>
      </div>
      <div style="height:6px;background:var(--gray-100);border-radius:100px;overflow:hidden;">
        <div style="height:100%;width:85%;background:var(--success);border-radius:100px;"></div>
      </div>
    </div>

    <div class="card card-pad" style="margin-bottom:16px;">
      <div style="font-size:15px;font-weight:700;color:var(--navy);margin-bottom:14px;">Application Summary</div>
      {#each [
        {k:'Status',v:'Ready to submit'},
        {k:'Documents',v:'3 attached'},
        {k:'Cover Letter',v:'Included'},
        {k:'Applied via',v:'Job Posting'},
      ] as s}
      <div style="display:flex;justify-content:space-between;padding:8px 0;border-bottom:1px solid var(--gray-100);font-size:13px;">
        <span style="color:var(--gray-400);">{s.k}</span>
        <span style="font-weight:600;color:var(--navy);">{s.v}</span>
      </div>
      {/each}
    </div>

    <button class="btn btn-outline btn-full" style="margin-bottom:10px;">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M1 12s4-8 11-8 11 8 11 8-4 8-11 8-11-8-11-8z"/><circle cx="12" cy="12" r="3"/></svg>
      Preview Application
    </button>
    <button class="btn btn-primary btn-full btn-lg" onclick={() => goto('/status')}>
      Submit Application
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="22" y1="2" x2="11" y2="13"/><polygon points="22 2 15 22 11 13 2 9 22 2"/></svg>
    </button>
  </aside>
</div>

<style>
  .app-layout { display: grid; grid-template-columns: 1fr 320px; gap: 24px; align-items: start; }
  @media (max-width: 900px) { .app-layout { grid-template-columns: 1fr; } }
</style>