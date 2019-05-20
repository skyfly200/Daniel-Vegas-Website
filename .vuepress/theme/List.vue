<template>
  <div class="base-layout">
    <Nav />
    <v-content>
      <v-container fluid>
        <v-layout class="pa-4 page-title">
          <h1>{{ $page.title }}</h1>
        </v-layout>
        <v-layout class="pa-4">
          <v-flex xs12 md10 offset-md1>
            <Content />
          </v-flex>
        </v-layout>
        <v-layout class="pa-4">
          <v-flex xs12 md10 offset-md1>
            <v-card class="pa-4">
              <ul>
                <template v-for="i in $page.frontmatter.list">
                  <li :key="i.title">
                    <h3>
                      <router-link v-if="i.type === 'work'" :to="i.path">{{ i.work }}</router-link>
                      <a v-if="i.type === 'external'" :href="i.url">{{ i.title }}</a>
                      <template v-else>{{ i.title }}</template>
                    </h3>
                    <p v-if="i.description">{{ i.description }}</p>
                  </li>
                </template>
              </ul>
            </v-card>
          </v-flex>
        </v-layout>
      </v-container>
    </v-content>
  </div>
</template>
<script>
import Nav from "./components/Nav"
export default {
  components: {
    Nav
  }
};
</script>
<style>
  .card-header {
    text-align: center;
  }
</style>
