<template>
  <div>
      <v-toolbar>
          <v-col cols="9">
              <v-toolbar-title>Guidelines</v-toolbar-title>
          </v-col>
          <v-col cols="2">
              <insertAddGuidelines />
          </v-col>
      </v-toolbar>
      <v-table fixed-header height="300px" width="100%">
          <thead>
              <tr>
                  <th class="text-left">
                      Page ID
                  </th>
                  <th class="text-left">
                      Page Name
                  </th>
                  <th class="text-left">
                      URL
                  </th>
                  <th class="text-left">
                      Meta Title
                  </th>
                  <th class="text-left">
                      Created
                  </th>
                  <th class="text-left">
                      Edit
                  </th>
              </tr>
          </thead>
          <tbody v-for="pages in findManyPages" :key="pages.id">
              <tr>
                  <td>{{ pages.id }}</td>
                  <td>{{ pages.title }}</td>
                  <td>{{ pages.url_key }}</td>
                  <td>{{ pages.meta_title }}</td>
                  <td>{{ pages.created_at }}</td>
                  <td><a :href="`/admin/database/${pages.id}`">
                          <!--<editUser />--></a></td>
              </tr>
          </tbody>
      </v-table>
  </div>
</template>

<script>
  import insertAddGuidelines from './guidelines/InsertAddGuidelines.vue'
  //import findManyPages from '../../../graphql/query/findManyPages.gql'

  export default {
      components: {
          insertAddGuidelines,
          //editUser
      },
      /*  data() {
          return {
              findManyPages: [],
          }
      },
      apollo: {
          findManyPages: {
              prefetch: true,
              query: findManyPages
          }
      }, */
  }
</script>

<script setup>
  useHead({
      title: 'Pages',
  })
</script>