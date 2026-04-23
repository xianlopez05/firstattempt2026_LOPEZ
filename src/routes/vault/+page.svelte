<script>
  let vaultLock = true;
</script>
<svelte:head><title>Digital Vault —  Job Posting</title></svelte:head>

<div class="hero-banner animate-in" style="margin-bottom:24px;">
  <div style="position:relative;z-index:1;display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:16px;">
    <div style="display:flex;align-items:center;gap:20px;">
      <div style="width:64px;height:64px;background:rgba(16,185,129,0.2);border-radius:50%;display:flex;align-items:center;justify-content:center;">
        <svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="#10B981" stroke-width="2"><rect x="3" y="11" width="18" height="11" rx="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/><circle cx="12" cy="16" r="1" fill="#10B981"/></svg>
      </div>
      <div>
        <div style="font-size:12px;color:rgba(255,255,255,0.4);font-weight:600;text-transform:uppercase;letter-spacing:0.5px;">Vault Status</div>
        <div style="font-size:22px;font-weight:700;color:white;">Encrypted & Secure</div>
        <div class="verified-pill" style="margin-top:6px;background:rgba(16,185,129,0.2);color:#6EE7B7;">✓ 3 Verified Records · AES-256</div>
      </div>
    </div>
    <div style="display:flex;gap:10px;">
      <button class="btn btn-outline" style="background:rgba(255,255,255,0.1);color:white;border-color:rgba(255,255,255,0.2);">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="7 10 12 15 17 10"/><line x1="12" y1="15" x2="12" y2="3"/></svg>
        Upload Document
      </button>
    </div>
  </div>
</div>

<div class="vault-grid animate-in" style="animation-delay:0.05s;">
  <div class="vault-main">
    <div class="card card-pad">
      <div class="section-header">
        <span class="section-title">Verified Records</span>
        <span style="background:rgba(37,99,235,0.1);color:var(--accent);font-size:12px;font-weight:700;padding:4px 12px;border-radius:100px;">3 Items</span>
      </div>

      {#each [
        {title:'e-Diploma',sub:'University of Excellence · 2023',type:'diploma',color:'rgba(37,99,235,0.1)',stroke:'#2563EB'},
        {title:'Academic Transcript',sub:'Official Grade Report',type:'transcript',color:'rgba(37,99,235,0.1)',stroke:'#2563EB'},
        {title:'AWS Cloud Practitioner',sub:'Certification ID: AWS-88219',type:'cert',color:'rgba(245,158,11,0.1)',stroke:'#D97706'},
      ] as item}
      <div class="vault-item">
        <div class="vault-icon" style="background:{item.color};">
          {#if item.type === 'cert'}
            <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke={item.stroke} stroke-width="2"><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/></svg>
          {:else}
            <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke={item.stroke} stroke-width="2"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14 2 14 8 20 8"/></svg>
          {/if}
        </div>
        <div style="flex:1;min-width:0;">
          <div style="font-size:15px;font-weight:600;color:var(--navy);">{item.title}</div>
          <div style="font-size:13px;color:var(--gray-400);margin-top:2px;">{item.sub}</div>
        </div>
        <div style="display:flex;gap:8px;align-items:center;">
          <button class="icon-btn"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="7 10 12 15 17 10"/><line x1="12" y1="15" x2="12" y2="3"/></svg></button>
          <button class="icon-btn"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="18" cy="5" r="3"/><circle cx="6" cy="12" r="3"/><circle cx="18" cy="19" r="3"/><line x1="8.59" y1="13.51" x2="15.42" y2="17.49"/></svg></button>
          <button class="btn btn-accent btn-sm">View</button>
        </div>
      </div>
      {/each}
    </div>
  </div>

  <aside class="vault-side">
    <div class="card card-pad" style="margin-bottom:16px;">
      <div style="font-size:15px;font-weight:700;color:var(--navy);margin-bottom:16px;">Security Settings</div>
      {#each [
        {label:'Vault Auto-Lock',sub:'Auto-locks after 5 minutes of inactivity',key:'lock'},
        {label:'Two-Factor Auth',sub:'Require 2FA when accessing vault',key:'2fa'},
        {label:'Access Log',sub:'Record all document access events',key:'log'},
      ] as s}
      <div style="display:flex;align-items:center;justify-content:space-between;padding:14px 0;border-bottom:1px solid var(--gray-100);">
        <div>
          <div style="font-size:14px;font-weight:600;color:var(--navy);">{s.label}</div>
          <div style="font-size:12px;color:var(--gray-400);margin-top:2px;">{s.sub}</div>
        </div>
        <label class="toggle">
          <input type="checkbox" checked={s.key === 'lock'} />
          <span class="toggle-slider"></span>
        </label>
      </div>
      {/each}
    </div>

    <div class="card card-pad">
      <div style="font-size:15px;font-weight:700;color:var(--navy);margin-bottom:14px;">Storage Used</div>
      <div style="font-size:28px;font-weight:700;color:var(--navy);margin-bottom:4px;">12.4 MB</div>
      <div style="font-size:13px;color:var(--gray-400);margin-bottom:10px;">of 500 MB used</div>
      <div style="height:8px;background:var(--gray-100);border-radius:100px;overflow:hidden;">
        <div style="height:100%;width:2.5%;background:var(--accent);border-radius:100px;"></div>
      </div>
    </div>
  </aside>
</div>

<style>
  .vault-grid { display: grid; grid-template-columns: 1fr 300px; gap: 24px; align-items: start; }
  @media (max-width: 900px) { .vault-grid { grid-template-columns: 1fr; } }
</style>