<template lang='html'>
  <div class="container">
      <div class="guide">
        <a href="https://linderoths.se/">
          <img alt="Linderoths" class="logo" width="120.99" height="19.787" style="margin-bottom: 2%;" src="https://linderoths.se/wp-content/uploads/2016/12/linderoths_logo.png"/>
        </a>
      </div>
      <div  style=" margin-bottom: 2em ;margin-top: 4%;">
        <p class="guide" style="font-family: 'Andale Mono', monospace; font-size: 11px;" v-if="name || titel || businessArea">
          <span style="color: #FC5961;"> • </span>
          <span>&nbsp;</span>
          <span style="color: #01215a;">{{name}}</span>
          <span>&nbsp;</span>
          <span style="color: #FC5961;"> • </span>
          <span>&nbsp;</span>
          <span style="color: #01215a;">{{titel}}</span>
          <span>&nbsp;</span>
          <span style="color: #FC5961;"> • </span>
          <span>&nbsp;</span>
          <span style="color: #01215a;">{{businessArea}}</span>
          
        </p>
        <div class="guide">
          <span style="color: #FC5961;" v-if="phone"> • </span>
          <span>&nbsp;</span>
          <a v-if="phone" style="color: #01215a;" :href="`tel:${phoneFormat}`">{{ phone }}</a>
          <span>&nbsp;</span>
          <span v-if="homepage" style="color: #FC5961;"> • </span>
          <span>&nbsp;</span>
          <a v-if="homepage" style="color: #FC5961;"  :href="`https://${hemsidan}`">{{ homepage }}</a>
          <span>&nbsp;</span>
          <span v-if="social" style="color: #FC5961;"> • </span>
          <span>&nbsp;</span>
          <span v-if="social" style="color: #01215a;">{{ social }}</span>
      </div>
      <div class="guide">
    <span v-if="local" style="color: #FC5961;"> • </span>
    <span>&nbsp;</span>
    <span v-if="local" style="color: #01215a;" >{{ local }}</span>
    <span>&nbsp;</span>
    <span v-if="street" style="color: #FC5961;">•</span>
    <span>&nbsp;</span>
    <span v-if="street" style="color: #01215a;" >{{ street }}</span>
    <span>&nbsp;</span>
    <span v-if="postNumber" style="color: #FC5961;">•</span>
    <span>&nbsp;</span>
    <span v-if="postNumber" style="color: #01215a;">{{ postNumber }}</span>
    <span>&nbsp;</span>
    <span v-if="city" style="color: #01215a;">{{ city }}</span>
      </div>
         </div>

    <div class="form">
      <div class="form-group">
        <div class="label guideFont ">
          <label for="formGroupExampleInput">Name:</label>
        </div>
        <input type="text" v-model="name" v-on:keyup="setName" class="form-control" id="formGroupExampleInput" placeholder="Firstname Lastname">
      </div>
      <div class="form-group">
        <div class="label guideFont">
          <label for="formGroupExampleInput2">Work Title:</label>
        </div>
        <input type="text" v-model="titel" v-on:keyup="setTitel" class="form-control" id="" placeholder="Work Title">
      </div>
      <div class="form-group">
        <div class="label guideFont">
           <label for="formGroupExampleInput">Business Area:</label>
        </div>
        <input type="text" v-model="businessArea" class="form-control" v-on:keyup="setBusinessArea" id="formGroupExampleInput" placeholder="Business Area">
      </div>
      <div class="form-group">
        <div class="label guideFont">
           <label for="formGroupExampleInput">Phone Number:</label>
        </div>
        <input type="text" v-model="phone" class="form-control" id="formGroupExampleInput" v-on:keyup="setPhone" placeholder="+46 7XX XX XX XX">
      </div>
      <div class="form-group">
        <div class="label guideFont">
           <label for="formGroupExampleInput">Home Page:</label>
        </div>
        <input v-model="homepage" type="text" class="form-control" id="formGroupExampleInput" v-on:keyup="setHomepage" placeholder="https://linderoths.se">
      </div>
      <div class="form-group">
        <div class="label guideFont">
            <label for="formGroupExampleInput">Social Media:</label>
        </div>
        <input v-model="social" type="text" class="form-control" id="formGroupExampleInput" v-on:keyup="setSocial" placeholder="@wearelinderoths">
      </div>
      <div class="form-group">
        <div class="label guideFont">
           <label for="formGroupExampleInput">Location:</label>
        </div>
        <input v-model="local" type="text" class="form-control" id="formGroupExampleInput" v-on:keyup="setLocal" placeholder="Victoriapassagen">
      </div>
      <div class="form-group">
        <div class="label guideFont">
           <label for="formGroupExampleInput">Street:</label>
        </div>
        <input v-model="street" type="text" class="form-control" id="formGroupExampleInput" v-on:keyup="setStreet" placeholder="Södra Larmgatan 14">
      </div>
      <div class="form-group">
        <div class="label guideFont">
             <label for="formGroupExampleInput">Post Number:</label>
        </div>
        <input v-model="postNumber" type="text" class="form-control" id="formGroupExampleInput" v-on:keyup="setPostNumber" placeholder="411 16">
      </div>
      <div class="form-group">
        <div class="label guideFont">
            <label for="formGroupExampleInput">City:</label>
        </div>
        <input v-model="city" type="text" class="form-control" id="formGroupExampleInput" v-on:keyup="setCity" placeholder="Göteborg">
      </div>
    </div>
    <div class="card guideFont guidecard">
      <div class="card-block guide">
        <h2 class="card-title guideColor">Guide:</h2>
      </div>
      <ul class="list-group list-group-flush">
        <li class="list-group-item">Use Chrome</li>
        <li class="list-group-item">Fill in the form</li>
        <li class="list-group-item">Text select the signature</li>
        <li class="list-group-item">Copy! Ctrl+C (pc) or CMD+C (mac)</li>
        <li class="list-group-item">Open Mail app, goto settings, then mail signature settings</li>
        <li class="list-group-item">Paste, save...</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      // click: false,
      name: localStorage.getItem('mail-signature_name') ? localStorage.getItem('mail-signature_name') : 'Förnamn Efternamn',
      titel: localStorage.getItem('mail-signature_titel') ? localStorage.getItem('mail-signature_titel') : 'Yrke',
      businessArea: localStorage.getItem('mail-signature_businessArea') ? localStorage.getItem('mail-signature_businessArea') : 'Affärsområde',
      phone: localStorage.getItem('mail-signature_phone') ? localStorage.getItem('mail-signature_phone') : '',
      phoneFormat: '',
      homepage: localStorage.getItem('mail-signature_homepage') ? localStorage.getItem('mail-signature_homepage') : 'https://linderoths.se',
      hemsidan: '',
      social: localStorage.getItem('mail-signature_social') ? localStorage.getItem('mail-signature_social') : '@wearelinderoths',
      local: localStorage.getItem('mail-signature_local') ? localStorage.getItem('mail-signature_local') : 'Victoriapassagen',
      street: localStorage.getItem('mail-signature_street') ? localStorage.getItem('mail-signature_street') : 'Södra Larmgatan 14',
      postNumber: localStorage.getItem('mail-signature_post') ? localStorage.getItem('mail-signature_post') : '411 16',
      city: localStorage.getItem('mail-signature_city') ? localStorage.getItem('mail-signature_city') : 'Göteborg'
    }
  },
  methods: {
    // buttonClick (ev) {
    //   // this.$refs.info.select()
    //   // document.execCommand('copy')
    // },
    setName () {
      localStorage.setItem('mail-signature_name', this.name)
    },
    setTitel () {
      localStorage.setItem('mail-signature_titel', this.titel)
    },
    setBusinessArea () {
      localStorage.setItem('mail-signature_businessArea', this.businessArea)
    },
    setPhone () {
      this.phoneFormat = this.phone.replace(/\s+/g, '')
      localStorage.setItem('mail-signature_phone', this.phone)
    },
    setHomepage () {
      var url = this.homepage
      this.hemsidan = url.replace('https://', '')
      localStorage.setItem('mail-signature_homepage', this.homepage)
    },
    setSocial () {
      localStorage.setItem('mail-signature_social', this.social)
    },
    setLocal () {
      localStorage.setItem('mail-signature_local', this.local)
    },
    setStreet () {
      localStorage.setItem('mail-signature_street', this.street)
    },
    setPostNumber () {
      localStorage.setItem('mail-signature_post', this.postNumber)
    },
    setCity () {
      localStorage.setItem('mail-signature_city', this.city)
    }
  }
}
</script>
