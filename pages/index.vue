<template>
  <v-row>
    <v-col
        v-for="card in cards"
        :key="card"
        cols="12"
    >
      <v-card>
        <v-subheader>{{ card }}</v-subheader>

        <v-list two-line>
          <template v-for="n in 6"
                    :key>
            <v-list-item v-if="n !== 0"
                         :key="n"
            >
              <v-list-item-avatar color="grey darken-1">
              </v-list-item-avatar>

              <v-list-item-content>
                <v-list-item-title>Message {{ n }}</v-list-item-title>

                <v-list-item-subtitle>
                  Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nihil repellendus distinctio similique
                </v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>

            <v-divider
                v-if="n !== 6"
                :key="`divider-${n}`"
                inset
            ></v-divider>
          </template>
        </v-list>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: "index.vue",
  data: () => ({
    cards: ['Today', 'Yesterday'],
    drawer: null,
  })
}
</script>
<style scoped>

</style>