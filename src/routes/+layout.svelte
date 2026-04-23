<script>
  import '../app.css';
  import { page } from '$app/stores';
  import { goto } from '$app/navigation';

  let sidebarOpen = false;

  const navLinks = [
    { href: '/profile', label: 'My Profile', icon: 'user', section: 'Alumni' },
    { href: '/jobs', label: 'Job Search', icon: 'search', section: 'Alumni' },
    { href: '/application', label: 'Apply', icon: 'send', section: 'Alumni' },
    { href: '/vault', label: 'Digital Vault', icon: 'lock', section: 'Alumni' },
    { href: '/status', label: 'App. Status', icon: 'activity', section: 'Alumni' },
    { href: '/employer', label: 'Dashboard', icon: 'grid', section: 'Employer' },
    { href: '/post', label: 'Post a Job', icon: 'plus-circle', section: 'Employer' },
    { href: '/screening', label: 'Screening', icon: 'users', section: 'Employer' },
  ];

  function isActive(href) {
    return $page.url.pathname === href || $page.url.pathname.startsWith(href + '/');
  }

  const isLoginPage = () => $page.url.pathname === '/' || $page.url.pathname === '/login';
</script>

{#if isLoginPage()}
  <slot />
{:else}
<!-- Sidebar overlay (mobile) -->
{#if sidebarOpen}
<div class="sidebar-overlay show" on:click={() => sidebarOpen = false} on:keydown={() => {}} role="button" tabindex="0"></div>
{/if}

<!-- Sidebar -->
<aside class="sidebar" class:open={sidebarOpen}>
  <div class="sidebar-logo">
    <a href="/profile" class="sidebar-logo-text" style="text-decoration:none;">Job Posting</a>
    <div class="sidebar-logo-sub">Job Posting Module</div>
  </div>

  <nav class="sidebar-nav">
    <div class="nav-section-label">Alumni</div>
    {#each navLinks.filter(l => l.section === 'Alumni') as link}
    <a href={link.href} class="nav-link" class:active={isActive(link.href)} on:click={() => sidebarOpen = false}>
      {#if link.icon === 'user'}
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="8" r="4"/><path d="M4 20c0-4 3.6-7 8-7s8 3 8 7"/></svg>
      {:else if link.icon === 'search'}
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="11" cy="11" r="8"/><line x1="21" y1="21" x2="16.65" y2="16.65"/></svg>
      {:else if link.icon === 'send'}
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="22" y1="2" x2="11" y2="13"/><polygon points="22 2 15 22 11 13 2 9 22 2"/></svg>
      {:else if link.icon === 'lock'}
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="11" width="18" height="11" rx="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/></svg>
      {:else if link.icon === 'activity'}
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/></svg>
      {/if}
      {link.label}
    </a>
    {/each}

    <div class="nav-section-label" style="margin-top:8px;">Employer</div>
    {#each navLinks.filter(l => l.section === 'Employer') as link}
    <a href={link.href} class="nav-link" class:active={isActive(link.href)} on:click={() => sidebarOpen = false}>
      {#if link.icon === 'grid'}
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="3" width="7" height="7"/><rect x="14" y="3" width="7" height="7"/><rect x="14" y="14" width="7" height="7"/><rect x="3" y="14" width="7" height="7"/></svg>
      {:else if link.icon === 'plus-circle'}
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"/><line x1="12" y1="8" x2="12" y2="16"/><line x1="8" y1="12" x2="16" y2="12"/></svg>
      {:else if link.icon === 'users'}
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/></svg>
      {/if}
      {link.label}
    </a>
    {/each}
  </nav>

  <div class="sidebar-footer">
    <div class="sidebar-user">
      <div class="avatar avatar-sm" style="background:linear-gradient(135deg,#667eea,#764ba2);">XN</div>
      <div>
        <div style="font-size:13px;font-weight:600;color:white;">Xian Lopez</div>
        <div style="font-size:11px;color:rgba(255,255,255,0.4);">Alumni · Class 2020</div>
      </div>
      <svg style="margin-left:auto;color:rgba(255,255,255,0.4);width:16px;height:16px;" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="9 18 15 12 9 6"/></svg>
    </div>
  </div>
</aside>

<!-- Main content -->
<div class="main-content">
  <!-- Desktop top nav -->
  <header class="top-nav">
    <div class="top-nav-title">
      {#if isActive('/profile')}My Profile
      {:else if isActive('/jobs')}Job Search
      {:else if isActive('/application')}Instant Application
      {:else if isActive('/vault')}Digital Vault
      {:else if isActive('/status')}Application Status
      {:else if isActive('/employer')}Employer Dashboard
      {:else if isActive('/post')}Post a Career Opportunity
      {:else if isActive('/screening')}Applicant Screening
      {:else}Job Posting
      {/if}
    </div>
    <div class="top-nav-actions">
      <button class="icon-btn"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" style="width:18px;height:18px;"><circle cx="11" cy="11" r="8"/><line x1="21" y1="21" x2="16.65" y2="16.65"/></svg></button>
      <button class="icon-btn"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" style="width:18px;height:18px;"><path d="M18 8A6 6 0 0 0 6 8c0 7-3 9-3 9h18s-3-2-3-9"/><path d="M13.73 21a2 2 0 0 1-3.46 0"/></svg></button>
      <div class="avatar avatar-sm" style="background:linear-gradient(135deg,#667eea,#764ba2);cursor:pointer;">XN</div>
    </div>
  </header>

  <!-- Mobile header -->
  <header class="mobile-header">
    <button class="icon-btn" on:click={() => sidebarOpen = !sidebarOpen}>
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="3" y1="12" x2="21" y2="12"/><line x1="3" y1="6" x2="21" y2="6"/><line x1="3" y1="18" x2="21" y2="18"/></svg>
    </button>
    <span class="mobile-logo">Job Posting</span>
    <button class="icon-btn"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M18 8A6 6 0 0 0 6 8c0 7-3 9-3 9h18s-3-2-3-9"/><path d="M13.73 21a2 2 0 0 1-3.46 0"/></svg></button>
  </header>

  <!-- Page content -->
  <main class="page-body">
    <slot />
  </main>
</div>

<!-- Mobile bottom nav -->
<nav class="mobile-bottom-nav">
  <a href="/jobs" class="mobile-nav-btn" class:active={isActive('/jobs')}>
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="11" cy="11" r="8"/><line x1="21" y1="21" x2="16.65" y2="16.65"/></svg>
    Search
  </a>
  <a href="/status" class="mobile-nav-btn" class:active={isActive('/status')}>
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14 2 14 8 20 8"/></svg>
    Applied
  </a>
  <a href="/vault" class="mobile-nav-btn" class:active={isActive('/vault')}>
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="11" width="18" height="11" rx="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/></svg>
    Vault
  </a>
  <a href="/profile" class="mobile-nav-btn" class:active={isActive('/profile')}>
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="8" r="4"/><path d="M4 20c0-4 3.6-7 8-7s8 3 8 7"/></svg>
    Profile
  </a>
</nav>
{/if}