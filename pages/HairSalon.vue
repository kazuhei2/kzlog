<template>
  <v-container>
    <v-row>
      <v-col class="text-center">
        <v-img
          :src="uploadImage"
          alt="Vuetify.js"
          class="mb-5"
        />
        <blockquote class="blockquote">
          &#8220;First, solve the problem. Then, write the code.&#8221;
          <footer>
            <small>
              <em>&mdash;Kazuhei Hamada</em>
            </small>
          </footer>
        </blockquote>
      </v-col>
    </v-row>
    <v-row align="center">
      <v-col cols="4">
        <v-subheader>Upload File</v-subheader>
      </v-col>
      <v-col cols="5">
        <v-file-input
          v-model="uploadFile"
          :rules="uploadFileRules"
          truncate-length="40"
        />
      </v-col>
      <v-col cols="3">
        <v-btn
          color="indigo"
          @click="onClickUpload"
        >
          <v-icon left>
            mdi-upload
          </v-icon>
          UPLOAD
        </v-btn>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'HairSalon',

  data() {
    return {
      uploadImage: null,
      uploadFile: null,
      uploadFileRules: [
        (f) => !!f || "There's no file.",
      ],
    }
  },

  methods: {
    onClickUpload() {
      const fr = new FileReader()
      fr.onload = async () => {
        this.uploadImage = fr.result
      }
      fr.readAsDataURL(this.uploadFile)
    },
  },
}
</script>
