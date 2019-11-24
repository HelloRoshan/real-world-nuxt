<template>
  <nav class="navbar" role="navigation" aria-label="main navigation">
    <div class="navbar-brand">
      <a
        role="button"
        class="navbar-burger"
        aria-label="menu"
        aria-expanded="false"
      >
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
      </a>
    </div>
    <div class="navbar-menu">
      <div class="navbar-start">
        Logo
      </div>
      <div class="navbar-end">
        <nuxt-link to="/" class="navbar-item">Home</nuxt-link>
        <div class="navbar-item has-dropdown is-hoverable">
          <a class="navbar-link">Projects</a>
          <div class="navbar-dropdown">
            <nuxt-link to="/vuet3" class="navbar-item">
              Vue Tic-Tac-Toe
            </nuxt-link>
          </div>
        </div>
        <nuxt-link to="/" class="navbar-item">Contact</nuxt-link>
      </div>
    </div>
  </nav>
</template>
