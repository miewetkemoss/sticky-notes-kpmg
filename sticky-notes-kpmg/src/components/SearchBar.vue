<template>
    <v-container>
        <v-row 
        class="d-flex align-center"
        cols="12">
            <v-text-field
            hide-details
            class="mt-8"
            placeholder="Quick Search"
            outlined/>
        
                <v-col>
                    <p>Types</p>
                    <v-btn-toggle mandatory>
                        <v-btn v-on:click="filterType('All')">All</v-btn>
                        <v-btn v-on:click="filterType('Task')">Tasks</v-btn>
                        <v-btn v-on:click="filterType('Reviewnote')">Notes</v-btn>
                    </v-btn-toggle>
                </v-col>
                
                <v-col>
                    <p>Priority</p>
                    <v-btn-toggle mandatory>
                        <v-btn>All</v-btn>
                        <v-btn>Low</v-btn>
                        <v-btn>Medium</v-btn>
                        <v-btn>High</v-btn>
                    </v-btn-toggle>
                </v-col>
                
                <v-col>
                    <p>Reporter</p>
                    <user-selection/>
                </v-col>

                <v-col>
                    <p>Assignees</p>
                    <user-selection/>
                </v-col>

                <v-col>
                    <p>Section</p>
                    <user-selection/>
                </v-col>

                <v-col>
                    <p>Date</p>
                    <v-menu
                    :close-on-content-click="true"
                    :nudge-left="40"
                    transition="scale-transition"
                    offset-y
                    outlined
                    min-width="auto"
                    >
                    <template v-slot:activator="{ on, attrs }">
                    <v-text-field
                        class="mt-8"
                        outlined
                        v-model="date"
                        prepend-icon="mdi-calendar"
                        readonly
                        v-bind="attrs"
                        v-on="on"
                    ></v-text-field>
                    </template>
                    <v-date-picker
                    v-model="date"
                    ></v-date-picker>
      </v-menu>

                </v-col>
        </v-row>
        <v-row>
            <a 
            class="d-flex align-self-end"
            href="http://localhost:8080/#/review-notes">
            Clear applied filters
            </a>
        </v-row>
        
    </v-container>
</template>

<script>
import UserSelection from './UserSelection.vue'

export default {
    components: { UserSelection },
    name: "SearchBar",
    methods: {
        filterType(str){
            this.$emit('filterTypes', str)
        }
    }
}
</script>