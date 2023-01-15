<template>
  <div>
    <table>
      <thead>
      <tr>
        <th>Number</th>
        <th>Name</th>
        <th>Group</th>
        <th>Telephone</th>
        <th>Participation</th>
        <th>Date</th>
        <th>Course</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="row in data" :key="row.Number">
        <td>{{ row.Number }}</td>
        <td>{{ row.Name }}</td>
        <td>{{ row.Group }}</td>
        <td>{{ row.Telephone }}</td>
        <td>{{ row.Participation }}</td>
        <td>{{ row.Date }}</td>
        <td>{{ row.Course }}</td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import { mapState } from 'vuex'
import {google} from 'googleapis'
const sheets = google.sheets('v4');


export default {
  name: "contacts.vue",
  data() {
    return {
      data: []
    }
  },
  computed: {
    ...mapState({
      googleAuth: state => state.googleAuth
    })
  },
 mounted() {
    // Initialize the Sheets API client
   async function sheetsApi() {

     const auth = await google.auth.getClient({ scopes: ['https://www.googleapis.com/auth/spreadsheets.readonly'] });

     const sheets = google.sheets({ version: 'v4', auth });
   }

    // Define the spreadsheet ID and range for the data you want to retrieve
    const spreadsheetId = '1ZkGElCf-Xl3CDvnTgeuZHrpIe8yy_cY552zrErr3xRs'
    const range = 'testing!A1:G35'

    // Use the Sheets API to retrieve the data
    sheetsApi.spreadsheets.values.get({
      spreadsheetId,
      range
    })
        .then(response => {
          let data = response.data.values;
          this.data = data.map(row => {
            return {
              Number: row[0],
              Name: row[1],
              Group: row[2],
              Telephone: row[3],
              Participation: row[4],
              Date: row[5],
              Course: row[6],
            }
          })
        })
        .catch(error => {
          console.log(error)
        })
  }
}
</script>