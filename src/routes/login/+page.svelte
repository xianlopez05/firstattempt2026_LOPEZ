<script>
  import { goto } from '$app/navigation';
  let loginTab = 'alumni';
  let email = '';
  let password = '';

  function handleSignIn() {
    goto('/profile');
  }
</script>

<svelte:head><title>Login — Job Posting</title></svelte:head>

<div class="login-page">
  <!-- Left panel (desktop only) -->
  <div class="login-left">
    <div class="login-left-content">
      <div class="login-brand">Job Posting</div>
      <h1 class="login-headline">Your verified career<br/>starts here.</h1>
      <p class="login-desc">Connect your academic records, skills, and career goals to opportunities that match — verified and trusted.</p>

      <div class="login-features">
        {#each [
          {icon:'shield','text':'University-verified credentials'},
          {icon:'zap','text':'AI-powered job matching'},
          {icon:'award','text':'Instant one-click applications'},
        ] as f}
        <div class="login-feature">
          <div class="login-feature-icon">
            {#if f.icon === 'shield'}
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/></svg>
            {:else if f.icon === 'zap'}
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polygon points="13 2 3 14 12 14 11 22 21 10 12 10 13 2"/></svg>
            {:else}
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="8" r="6"/><path d="M15.477 12.89L17 22l-5-3-5 3 1.523-9.11"/></svg>
            {/if}
          </div>
          <span>{f.text}</span>
        </div>
        {/each}
      </div>
    </div>
    <div class="login-left-footer">© 2026 Job Posting · Privacy · Terms</div>
  </div>

  <!-- Right panel - login form -->
  <div class="login-right">
    <div class="login-form-wrap">
      <div class="login-form-brand">Job Posting</div>
      <h2 class="login-form-title">Welcome back</h2>
      <p class="login-form-sub">Access your professional network and career tools.</p>

      <!-- Tabs -->
      <div class="login-tabs">
        <button class="login-tab" class:active={loginTab === 'alumni'} onclick={() => loginTab = 'alumni'}>Alumni</button>
        <button class="login-tab" class:active={loginTab === 'employer'} onclick={() => loginTab = 'employer'}>Employer</button>
        <button class="login-tab" class:active={loginTab === 'staff'} onclick={() => loginTab = 'staff'}>Staff</button>
      </div>

      <div class="form-group">
        <label class="form-label">Email or ID</label>
        <div class="input-wrap">
          <svg class="input-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="2" y="4" width="20" height="16" rx="2"/><path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"/></svg>
          <input class="form-input" type="email" placeholder="Enter your email or ID" bind:value={email} />
        </div>
      </div>

      <div class="form-group">
        <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:6px;">
          <label class="form-label" style="margin:0;">Password</label>
          <span class="section-link" style="font-size:13px;">Forgot Password?</span>
        </div>
        <div class="input-wrap">
          <svg class="input-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="11" width="18" height="11" rx="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/></svg>
          <input class="form-input" type="password" placeholder="••••••••" bind:value={password} />
        </div>
      </div>

      <button class="btn btn-primary btn-full btn-lg" onclick={handleSignIn}>
        Sign In
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><path d="M15 3h4a2 2 0 0 1 2 2v14a2 2 0 0 1-2 2h-4"/><polyline points="10 17 15 12 10 7"/><line x1="15" y1="12" x2="3" y2="12"/></svg>
      </button>

      <div class="divider-text">OR CONTINUE WITH</div>

      <button class="btn btn-outline btn-full" style="margin-bottom:10px;">
        <svg viewBox="0 0 24 24" width="18" height="18"><path fill="#4285F4" d="M22.56 12.25c0-.78-.07-1.53-.2-2.25H12v4.26h5.92c-.26 1.37-1.04 2.53-2.21 3.31v2.77h3.57c2.08-1.92 3.28-4.74 3.28-8.09z"/><path fill="#34A853" d="M12 23c2.97 0 5.46-.98 7.28-2.66l-3.57-2.77c-.98.66-2.23 1.06-3.71 1.06-2.86 0-5.29-1.93-6.16-4.53H2.18v2.84C3.99 20.53 7.7 23 12 23z"/><path fill="#FBBC05" d="M5.84 14.09c-.22-.66-.35-1.36-.35-2.09s.13-1.43.35-2.09V7.07H2.18C1.43 8.55 1 10.22 1 12s.43 3.45 1.18 4.93l2.85-2.22.81-.62z"/><path fill="#EA4335" d="M12 5.38c1.62 0 3.06.56 4.21 1.64l3.15-3.15C17.45 2.09 14.97 1 12 1 7.7 1 3.99 3.47 2.18 7.07l3.66 2.84c.87-2.6 3.3-4.53 6.16-4.53z"/></svg>
        Sign in with Google
      </button>
      <button class="btn btn-outline btn-full">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="18" height="18"><rect x="2" y="6" width="20" height="12" rx="2"/><path d="M12 12h.01M8 12h.01M16 12h.01"/></svg>
        Single Sign-On (SSO)
      </button>

      <p style="text-align:center;margin-top:24px;font-size:14px;color:var(--gray-400);">
        New to Job Posting? <span class="section-link" style="font-weight:600;">Request Access</span>
      </p>
    </div>
  </div>
</div>

<style>
  .login-page {
    min-height: 100vh;
    display: flex;
    background: white;
  }

  /* Left panel */
  .login-left {
    flex: 1;
    background: linear-gradient(165deg, #0D1B3E 0%, #1E3A6E 100%);
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    padding: 48px 56px;
    min-height: 100vh;
    position: relative;
    overflow: hidden;
  }

  .login-left::before {
    content: '';
    position: absolute;
    inset: 0;
    background: url("data:image/svg+xml,%3Csvg width='80' height='80' viewBox='0 0 80 80' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='none' fill-rule='evenodd'%3E%3Cg fill='%23ffffff' fill-opacity='0.03'%3E%3Cpath d='M0 0h40v40H0V0zm40 40h40v40H40V40zm0-40h2l-2 2V0zm0 4l4-4h2l-6 6V4zm0 4l8-8h2L40 10V8zm0 4L52 0h2L40 14v-2zm0 4L56 0h2L40 18v-2zm0 4L60 0h2L40 22v-2zm0 4L64 0h2L40 26v-2zm0 4L68 0h2L40 30v-2zm0 4L72 0h2L40 34v-2zm0 4L76 0h2L40 38v-2zm0 4L80 0v2L42 40h-2zm4 0L80 4v2L46 40h-2zm4 0L80 8v2L50 40h-2zm4 0l28-28v2L54 40h-2zm4 0l24-24v2L58 40h-2zm4 0l20-20v2L62 40h-2zm4 0l16-16v2L66 40h-2zm4 0l12-12v2L70 40h-2zm4 0l8-8v2l-6 6h-2zm4 0l4-4v2l-2 2h-2z'/%3E%3C/g%3E%3C/g%3E%3C/svg%3E");
  }

  .login-left-content { position: relative; z-index: 1; }

  .login-brand {
    font-family: 'DM Serif Display', serif;
    font-size: 22px;
    color: white;
    margin-bottom: 56px;
  }

  .login-headline {
    font-family: 'DM Serif Display', serif;
    font-size: 42px;
    color: white;
    line-height: 1.2;
    margin-bottom: 20px;
  }

  .login-desc {
    font-size: 16px;
    color: rgba(255,255,255,0.6);
    line-height: 1.7;
    margin-bottom: 48px;
    max-width: 380px;
  }

  .login-features { display: flex; flex-direction: column; gap: 16px; }

  .login-feature {
    display: flex;
    align-items: center;
    gap: 14px;
    color: rgba(255,255,255,0.8);
    font-size: 15px;
    font-weight: 500;
  }

  .login-feature-icon {
    width: 40px;
    height: 40px;
    background: rgba(255,255,255,0.1);
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
  }
  .login-feature-icon svg { width: 20px; height: 20px; }

  .login-left-footer {
    position: relative;
    z-index: 1;
    font-size: 13px;
    color: rgba(255,255,255,0.3);
  }

  /* Right panel */
  .login-right {
    width: 480px;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 48px 40px;
    background: white;
    overflow-y: auto;
  }

  .login-form-wrap { width: 100%; max-width: 380px; }

  .login-form-brand {
    font-family: 'DM Serif Display', serif;
    font-size: 18px;
    color: var(--navy);
    margin-bottom: 28px;
    display: none; /* hidden on desktop, shown on mobile */
  }

  .login-form-title {
    font-size: 28px;
    font-weight: 700;
    color: var(--navy);
    margin-bottom: 6px;
  }

  .login-form-sub { font-size: 14px; color: var(--gray-400); margin-bottom: 28px; }

  /* Tabs */
  .login-tabs {
    display: flex;
    background: var(--gray-100);
    border-radius: 10px;
    padding: 4px;
    margin-bottom: 24px;
  }

  .login-tab {
    flex: 1;
    padding: 9px;
    border: none;
    background: none;
    border-radius: 8px;
    font-size: 14px;
    font-weight: 500;
    color: var(--gray-400);
    cursor: pointer;
    font-family: 'DM Sans', sans-serif;
    transition: all 0.2s;
  }

  .login-tab.active {
    background: white;
    color: var(--navy);
    box-shadow: 0 1px 4px rgba(0,0,0,0.1);
    font-weight: 600;
  }

  /* Mobile responsive */
  @media (max-width: 900px) {
    .login-page { flex-direction: column; }
    .login-left {
      min-height: auto;
      padding: 40px 28px 48px;
    }
    .login-headline { font-size: 28px; }
    .login-features { display: none; }
    .login-right {
      width: 100%;
      padding: 32px 24px 48px;
      align-items: flex-start;
    }
    .login-form-brand { display: block; }
    .login-form-title { font-size: 22px; }
    .login-left-footer { display: none; }
  }
</style>