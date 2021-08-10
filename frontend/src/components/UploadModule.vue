<template>
<div class="container">
    <div class="large-12 medium-12 small-12 cell">
      <label>File
        <input type="file" id="file" ref="file" v-on:change="handleFileUpload()"/>
      </label>
        <button v-on:click="submitFile()">Upload script</button>
    </div>
  </div>
</template>

<script>
import axios from "axios"
export default {
  name: 'UploadModule',
  props: {
    msg: String
  },
  methods: {
    submitFile() {
    let hostPortTerraformServer = "http://178.170.195.224:8080";
    let endpointTerraformServer = "/terraform/run/script";
    let url = hostPortTerraformServer + endpointTerraformServer;
    let formData = new FormData();
    formData.append('scriptFile', this.file);
    axios.post(url,
            formData, {
                headers: {
                    'Content-Type': 'form-data'
                }
            }
        ).then(function() {
            console.log('SUCCESS!!');
        })
        .catch(function() {
            console.log('FAILURE!!');
        });
},
    handleFileUpload() {
      this.file = this.$refs.file.files[0];
      return null;
    }

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
