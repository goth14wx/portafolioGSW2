<template>
    <v-content >
      <v-container
        class="fill-height"
        fluid
      >
        <v-row
          align="center"
          justify="center"
        >
          <v-col
            cols="12"
            sm="8"
            md="4"
          >
            <v-card  >
              <v-toolbar
                dark
                flat
              >
                <v-toolbar-title>Bienvenido</v-toolbar-title>
                <div class="flex-grow-1"></div>

              </v-toolbar>
              <v-card-text>
                <v-form>
                    <v-tooltip right>
                  <template v-slot:activator="{ on }">
                      <v-text-field
                    label="Correo Electronico Completo"
                    name="login"
                    type="email"
                    prepend-icon="email"
                  ></v-text-field>
                  </template>
                  <span>Correo Electronico</span>
                    </v-tooltip>
                  <v-text-field
                    id="password"
                    label="Contaseña"
                    name="password"
                    prepend-icon="lock"
                  ></v-text-field>
                </v-form>
              </v-card-text>
              <v-card-actions>
                <div class="flex-grow-1"></div>
                <v-btn >Login</v-btn>
              </v-card-actions>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-content>
</template>
