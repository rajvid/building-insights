<template>
  <div id="app">
    <b-container fluid class="sticky-top" id="header-container">
      <b-row>
        <b-col md="10" offset-md="1">
          <b-navbar toggleable="lg" id="navbar-toggle" variant="faded">
            <b-navbar-brand href="#">
              <img src="@/assets/images/logo-img.png" alt="Building Insights Logo">
            </b-navbar-brand>
            <b-navbar-toggle target="navbar-toggle-collapse">
                  <template #default="{ expanded }">
                    <b-icon v-if="expanded" icon="chevron-bar-up"></b-icon>
                    <b-icon v-else icon="chevron-bar-down"></b-icon>
                  </template>
            </b-navbar-toggle>
            <b-collapse id="navbar-toggle-collapse" is-nav>
              <b-navbar-nav id="navbar-toggle-link" class="ml-auto">
                <b-nav-item to="/">Home</b-nav-item>
                <b-nav-item to="/Portfolio">Portfolio</b-nav-item>
                <b-nav-item to="/Books">Resources</b-nav-item>
                <b-nav-item to="/Earthquakes">Earthquakes</b-nav-item>
                <b-nav-item to="/Contact">Contact Us</b-nav-item>
              </b-navbar-nav>
            </b-collapse>
          </b-navbar>
          <p class="px-3 font-italic" id="tagline">"Envision a taller and a safer future with us!"</p>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<style lang="scss">
// Importing partials here
@import '@/assets/styles/_base.normalize.scss';
@import '@/assets/styles/_components.content.scss';
@import '@/assets/styles/_settings.responsive.scss';
@import '@/assets/styles/_settings.variables.scss';

//Navbar styling

#header-container {
  background-color: $white;
}

#tagline {
  text-transform: capitalize;
}

#navbar-toggle {
  img {
    height: 100px;
  }

  &-link {
    text-align: left;
    a, .nuxt-link {
      font-weight: normal;
      color: $black;
      text-decoration: none;
      text-align: start;
      margin: 0 1rem;
      padding: 0 1rem;
      @include media-query("mobile") {
        margin: 0.5rem 0;
        &:hover {
          background-color: $black;
          color: $gray;
        }
      }
      &.nuxt-link-exact-active, &:hover {
        color: $gray;
      }
    }
  }
}
</style>
