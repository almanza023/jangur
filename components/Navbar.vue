<template>
  <div>
    <div>
  <b-navbar toggleable="lg" type="dark" variant="info">
    <b-navbar-brand href="#">JANGUR</b-navbar-brand>

    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

    <b-collapse id="nav-collapse" is-nav>
      <b-navbar-nav>
        <b-nav-item href="/sesion1">Sesión 1</b-nav-item>
        <b-nav-item href="/sesion1m2">Sesión 1 M2</b-nav-item>
        <b-nav-item href="/sesion2">Sesión 2</b-nav-item>
        <b-nav-item href="/sesion3">Sesión 3</b-nav-item>
        <b-nav-item href="/sesion4">Sesión 4</b-nav-item>
     </b-navbar-nav>

      <!-- Right aligned nav items -->
      <b-navbar-nav class="ml-auto">

        <b-nav-item-dropdown right>
          <!-- Using 'button-content' slot -->
          <template #button-content>
            <em>User</em>
          </template>
          <b-dropdown-item href="#">Profile</b-dropdown-item>
          <b-dropdown-item href="#">Sign Out</b-dropdown-item>
        </b-nav-item-dropdown>
      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
</div>
  </div>
</template>
