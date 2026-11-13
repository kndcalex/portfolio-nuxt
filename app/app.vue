<template>
  <div class="min-h-screen bg-base-100 text-base-content">
    <NuxtRouteAnnouncer />
    <AppHeader />
    <div class="mx-auto flex w-full max-w-7xl gap-8 px-4 pb-10 pt-24 sm:px-6 lg:px-8">
      <DesktopSidebar />
      <main id="main-content" class="min-w-0 flex-1">
        <NuxtPage />
        <AppFooter />
      </main>
    </div>
  </div>
</template>
