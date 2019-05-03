<template>
<v-footer class="blue darken-2">
    <v-layout row wrap align-center>
        <v-flex xs12>
            <div class="white--text ml-3">
                &copy; {{ getYear }}
            </div>
        </v-flex>
    </v-layout>
</v-footer>
</template>

<script>

  export default {
    data: () => ({

    }),
    computed: {
      getYear () {
        const today = new Date();
        return today.getFullYear();
      }
    }
  }

</script>
