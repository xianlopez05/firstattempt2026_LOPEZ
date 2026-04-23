<svelte:head><title>Application Status — Job Posting</title></svelte:head>

<div class="animate-in">
  <div class="status-layout">
    <div class="status-main">
      <div class="card card-pad" style="margin-bottom:20px;">
        <div style="display:flex;align-items:center;gap:16px;margin-bottom:20px;">
          <div class="company-logo" style="background:#4285F4;width:60px;height:60px;font-size:18px;border-radius:14px;">G</div>
          <div>
            <h2 style="font-size:20px;font-weight:700;color:var(--navy);">Senior Software Engineer</h2>
            <div style="font-size:14px;color:var(--gray-400);">Google · Mountain View, CA</div>
          </div>
          <div style="margin-left:auto;background:rgba(37,99,235,0.1);color:var(--accent);padding:6px 14px;border-radius:100px;font-size:13px;font-weight:700;">In Progress</div>
        </div>

        <!-- Progress steps -->
        <div class="timeline-steps">
          <div class="step-col"><div class="step-dot done">✓</div><div class="step-line done"></div></div>
          <div class="step-col"><div class="step-dot done">✓</div><div class="step-line done"></div></div>
          <div class="step-col"><div class="step-dot done">✓</div><div class="step-line"></div></div>
          <div class="step-col"><div class="step-dot current">💬</div><div class="step-line"></div></div>
          <div class="step-dot pending">🏢</div>
        </div>
        <div style="display:flex;justify-content:space-between;margin-top:8px;">
          {#each ['Applied','Viewed','Shortlisted','Interview','Hired'] as s, i}
          <span style="font-size:10px;font-weight:700;color:{i === 3 ? 'var(--accent)' : 'var(--gray-400)'};text-align:center;flex:1;">{s.toUpperCase()}</span>
          {/each}
        </div>
      </div>

      <!-- Recruiter message -->
      <div class="card card-pad" style="margin-bottom:20px;">
        <div style="display:flex;align-items:center;gap:12px;margin-bottom:14px;">
          <div class="avatar avatar-md" style="background:linear-gradient(135deg,#F59E0B,#EF4444);">SJ</div>
          <div>
            <div style="font-size:15px;font-weight:700;color:var(--navy);">Sarah Jenkins</div>
            <div style="font-size:13px;color:var(--gray-400);">Senior Technical Recruiter · Google</div>
          </div>
          <button class="btn btn-outline btn-sm" style="margin-left:auto;">Reply</button>
        </div>
        <div class="message-bubble">"Hi Xian! Great news – the team was really impressed with your portfolio. We'd like to move forward with a technical interview. Are you available this Thursday?"</div>
      </div>

      <!-- Timeline -->
      <div class="card card-pad">
        <div style="font-size:17px;font-weight:700;color:var(--navy);margin-bottom:16px;">Timeline of Events</div>
        {#each [
          {title:'Interview Invitation Sent',time:'Today, 10:45 AM',done:true},
          {title:'Application Shortlisted',time:'Yesterday, 02:15 PM',done:true},
          {title:'Resume Viewed by Hiring Manager',time:'Oct 24, 2023',done:false},
          {title:'Application Submitted',time:'Oct 22, 2023',done:false},
        ] as ev, i}
        <div style="display:flex;gap:14px;margin-bottom:16px;position:relative;">
          {#if i < 3}
          <div style="position:absolute;left:4.5px;top:14px;width:1px;height:calc(100% + 4px);background:var(--gray-200);z-index:0;"></div>
          {/if}
          <div style="width:10px;height:10px;border-radius:50%;background:{ev.done ? 'var(--navy)' : 'var(--gray-300)'};flex-shrink:0;margin-top:4px;position:relative;z-index:1;"></div>
          <div>
            <div style="font-size:14px;font-weight:600;color:{ev.done ? 'var(--navy)' : 'var(--gray-600)'};">{ev.title}</div>
            <div style="font-size:12px;color:var(--gray-400);">{ev.time}</div>
          </div>
        </div>
        {/each}
      </div>
    </div>

    <aside class="status-side">
      <div class="card card-pad" style="margin-bottom:16px;">
        <div style="font-size:15px;font-weight:700;color:var(--navy);margin-bottom:14px;">All Applications</div>
        {#each [
          {co:'Google',role:'Sr. Software Engineer',status:'Interview',color:'#4285F4',abbr:'G'},
          {co:'Meta',role:'Product Manager',status:'Viewed',color:'#1877F2',abbr:'M'},
          {co:'Stripe',role:'Data Analyst',status:'Applied',color:'#635BFF',abbr:'S'},
        ] as app}
        <div style="display:flex;align-items:center;gap:10px;padding:10px 0;border-bottom:1px solid var(--gray-100);cursor:pointer;">
          <div class="company-logo" style="background:{app.color};width:36px;height:36px;font-size:11px;">{app.abbr}</div>
          <div style="flex:1;min-width:0;">
            <div style="font-size:13px;font-weight:600;color:var(--navy);white-space:nowrap;overflow:hidden;text-overflow:ellipsis;">{app.role}</div>
            <div style="font-size:12px;color:var(--gray-400);">{app.co}</div>
          </div>
          <span style="font-size:11px;font-weight:700;color:var(--accent);background:rgba(37,99,235,0.1);padding:3px 8px;border-radius:100px;white-space:nowrap;">{app.status}</span>
        </div>
        {/each}
      </div>
    </aside>
  </div>
</div>

<style>
  .status-layout { display: grid; grid-template-columns: 1fr 280px; gap: 24px; align-items: start; }
  @media (max-width: 900px) { .status-layout { grid-template-columns: 1fr; } }
</style>