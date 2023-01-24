<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card>
        <v-card-title class="headline">
          ユーザー一覧
        </v-card-title>
        <v-card-text>
          <v-simple-table>
            <thead>
              <tr>
                <th>ユーザー名</th>
                <th>仕事</th>
                <th>趣味</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="user in users" :key="user.id">
                <th>{{ user.name }}</th>
                <th>{{ user.work }}</th>
                <th>{{ user.hobby }}</th>
              </tr>
            </tbody>
          </v-simple-table>
        </v-card-text>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
// import 'vue-apollo';
import usersQuery from '../apollo/queries/users.gql';

export default {
  name: 'IndexPage',
  data() {
    return {
      users: [],
    };
  },
  apollo: {
    users: {
      prefetch: true,
      query: usersQuery,
    },
  },
};
</script>
