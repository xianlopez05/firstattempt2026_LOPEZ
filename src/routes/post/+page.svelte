<script>
  import { goto } from '$app/navigation';
  let step = 1;
  let locationPref = 'onsite';
  let salaryToggle = true;
  let alumniToggle = false;
</script>
<svelte:head><title>Post a Career Opportunity — Job Posting</title></svelte:head>

<div class="post-layout animate-in">
  <div class="post-main">
    <!-- Step indicators -->
    <div class="card card-pad" style="margin-bottom:24px;">
      <div style="display:flex;gap:0;margin-bottom:20px;">
        {#each [1,2,3,4] as s}
        <div style="flex:1;display:flex;align-items:center;">
          <div style="width:32px;height:32px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:13px;font-weight:700;background:{s <= step ? 'var(--navy)' : 'var(--gray-200)'};color:{s <= step ? 'white' : 'var(--gray-400)'};flex-shrink:0;z-index:1;">{s}</div>
          {#if s < 4}
          <div style="flex:1;height:2px;background:{s < step ? 'var(--navy)' : 'var(--gray-200)'};"></div>
          {/if}
        </div>
        {/each}
      </div>
      <div style="display:flex;justify-content:space-between;">
        {#each ['Basic Info','Description','Requirements','Review'] as label, i}
        <span style="font-size:11px;font-weight:600;color:{i + 1 === step ? 'var(--navy)' : 'var(--gray-400)'};text-align:center;flex:1;">{label}</span>
        {/each}
      </div>
    </div>

    <div class="card card-pad">
      <h2 style="font-size:22px;font-weight:700;color:var(--navy);margin-bottom:4px;">Basic Information</h2>
      <p style="font-size:14px;color:var(--gray-400);margin-bottom:24px;">Step 1 of 4: Tell us the fundamentals of the role you're hiring for.</p>

      <div class="form-group">
        <label class="form-label">Job Title</label>
        <input type="text" class="form-input form-input-bare" placeholder="e.g. Senior Product Designer" />
      </div>

      <div class="grid-2" style="margin-bottom:20px;">
        <div class="form-group" style="margin-bottom:0;">
          <label class="form-label">Employment Type</label>
          <select class="form-input">
            <option>Select employment type</option>
            <option>Full-time</option>
            <option>Part-time</option>
            <option>Contract</option>
            <option>Internship</option>
          </select>
        </div>
        <div class="form-group" style="margin-bottom:0;">
          <label class="form-label">Department</label>
          <select class="form-input">
            <option>Select department</option>
            <option>Engineering</option>
            <option>Product</option>
            <option>Design</option>
            <option>Marketing</option>
          </select>
        </div>
      </div>

      <div class="form-group">
        <label class="form-label">Location Preference</label>
        <div style="display:flex;gap:12px;">
          {#each [
            {val:'onsite',label:'On-site',icon:'building'},
            {val:'remote',label:'Remote',icon:'home'},
            {val:'hybrid',label:'Hybrid',icon:'map'},
          ] as l}
          <button class="loc-opt" class:selected={locationPref === l.val} onclick={() => locationPref = l.val}>
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              {#if l.icon === 'building'}
                <rect x="2" y="7" width="20" height="14" rx="2"/><path d="M16 7V5a2 2 0 0 0-2-2h-4a2 2 0 0 0-2 2v2"/>
              {:else if l.icon === 'home'}
                <path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"/>
              {:else}
                <path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"/><circle cx="12" cy="10" r="3"/>
              {/if}
            </svg>
            {l.label}
          </button>
          {/each}
        </div>
      </div>

      <div class="divider"></div>

      <div style="display:flex;align-items:center;justify-content:space-between;padding:14px 0;border-bottom:1px solid var(--gray-100);">
        <div>
          <div style="font-size:14px;font-weight:600;color:var(--navy);">Show salary range</div>
          <div style="font-size:12px;color:var(--gray-400);margin-top:2px;">Recommended for 2× more applications</div>
        </div>
        <label class="toggle"><input type="checkbox" bind:checked={salaryToggle}/><span class="toggle-slider"></span></label>
      </div>

      <div style="display:flex;align-items:center;justify-content:space-between;padding:14px 0;">
        <div>
          <div style="font-size:14px;font-weight:600;color:var(--navy);">Alumni Exclusive</div>
          <div style="font-size:12px;color:var(--gray-400);margin-top:2px;">Only show this role to verified alumni</div>
        </div>
        <label class="toggle"><input type="checkbox" bind:checked={alumniToggle}/><span class="toggle-slider"></span></label>
      </div>

      <div class="divider"></div>

      <div style="display:flex;gap:12px;justify-content:flex-end;">
        <button class="btn btn-outline" onclick={() => goto('/employer')}>Cancel</button>
        <button class="btn btn-primary" onclick={() => goto('/employer')}>
          Continue to Description
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="9 18 15 12 9 6"/></svg>
        </button>
      </div>
      <p style="text-align:center;font-size:12px;color:var(--gray-400);margin-top:10px;">Drafts are saved automatically as you type.</p>
    </div>
  </div>

  <aside class="post-side">
    <div class="card card-pad" style="margin-bottom:16px;">
      <div style="font-size:15px;font-weight:700;color:var(--navy);margin-bottom:14px;">Hiring Team</div>
      {#each [
        {i:'XN',bg:'linear-gradient(135deg,#667eea,#764ba2)',name:'Xian Lopez'},
        {i:'SM',bg:'linear-gradient(135deg,#F59E0B,#EF4444)',name:'Sarah Miller'},
        {i:'DC',bg:'linear-gradient(135deg,#10B981,#3B82F6)',name:'David Chen'},
      ] as m}
      <div style="display:flex;align-items:center;gap:10px;padding:8px 0;border-bottom:1px solid var(--gray-100);">
        <div class="avatar avatar-sm" style="background:{m.bg};">{m.i}</div>
        <span style="font-size:14px;color:var(--navy);font-weight:500;">{m.name}</span>
      </div>
      {/each}
      <button class="btn btn-outline btn-full btn-sm" style="margin-top:12px;">+ Add Team Member</button>
    </div>

    <div class="card card-pad">
      <div style="font-size:15px;font-weight:700;color:var(--navy);margin-bottom:14px;">Tips</div>
      {#each ['Include salary range to get 2× more applicants','Alumni Exclusive roles fill 30% faster','Clear job titles increase visibility by 50%'] as tip}
      <div style="display:flex;gap:10px;padding:10px 0;border-bottom:1px solid var(--gray-100);font-size:13px;color:var(--gray-600);">
        <span style="color:var(--success);flex-shrink:0;">✓</span>
        {tip}
      </div>
      {/each}
    </div>
  </aside>
</div>

<style>
  .post-layout { display: grid; grid-template-columns: 1fr 280px; gap: 24px; align-items: start; }
  @media (max-width: 900px) { .post-layout { grid-template-columns: 1fr; } .post-side { display: none; } }
</style>