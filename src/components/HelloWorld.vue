<template>
  <v-container>
    <div id="file-app">
      <v-app>
        <v-app-bar app color="indigo" dark>
          <v-toolbar-title>{{title}}</v-toolbar-title>
        </v-app-bar>
        <v-content>
          <v-container>
            <!-- <v-layout align-center justify-center> -->
            <v-row>
              <v-col class="text-center" cols="12" sm="4" hidden>
                <v-file-input
                  multiple
                  label="File input"
                  id="file-upload"
                  v-model="files"
                  @change="fileUpload"
                />
              </v-col>
              <v-col>
                <v-btn @click="loadingFile" large>File Upload</v-btn>
              </v-col>
              <v-col>
                <v-text-field :value="file_name" disabled />
              </v-col>
            </v-row>
            <!-- </v-layout> -->
          </v-container>
        </v-content>
      </v-app>
    </div>
  </v-container>
</template> 

<script>
export default {
  name: "HelloWorld",
  props: {
    title: {
      type: String,
      default: "Application"
    }
  },

  data: () => ({
    files: null,
    file_name: ""
  }),
  methods: {
    loadingFile: event => {
      event.preventDefault();
      document.getElementById("file-upload").click();
    },
    fileUpload: function(event) {
      //  var filesCollections = event.target.value;
      if (event[0]) {
        console.log("Upload File: ", event[0]);
        this.file_name = event[0].name;
        console.log(this.file_name);
      }
    }
  }
};
</script>
