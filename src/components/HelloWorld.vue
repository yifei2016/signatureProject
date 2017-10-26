<template lang='html'>
  <div class="container">
      <div class="guide">
        <a href="https://www.fullystudios.se">
          <img alt="Fully Studios" class="logo" src="https://linderoths.se/wp-content/uploads/2016/12/linderoths_logo.png"/>
        </a>
      </div>
      <div class="textInfo" >
        <p class="guide" v-if="name || titel || businessArea">
          <span class="dotColor"> • </span>
          <span>&nbsp;</span>
          <span class="instance">{{name}}</span><span>&nbsp;</span>
          <span class="dotColor"> • </span>
          <span>&nbsp;</span>
          <span class="instance">{{titel}}<span>&nbsp;</span></span>
          <span>&nbsp;</span>
          <span class="instance">{{businessArea}}</span>
        </p>
        <div class="guide">
          <span class="dotColor" v-if="phone"> • </span>
          <span>&nbsp;</span>
          <a v-if="phone" class="instance" :href="`tel:${phone}`">{{ phone }}</a>
          <span>&nbsp;</span>
          <span v-if="homepage" class="dotColor"> • </span>
          <span>&nbsp;</span>
          <a v-if="homepage" class="dotColor"  :href="`https://${homepage}`">{{ homepage }}</a>
          <span>&nbsp;</span>
          <span v-if="social" class="dotColor"> • </span>
          <span>&nbsp;</span>
          <span v-if="social" class="instance">{{social}}</span>
        </div>
        <div class="guide">
          <span v-if="local" class="dotColor"> • </span>
          <span>&nbsp;</span>
          <span v-if="local" class="instance" >{{ local }}</span>
          <span>&nbsp;</span>
          <span v-if="street" class="dotColor"> • </span>
          <span>&nbsp;</span>
          <span v-if="street" class="instance" >{{ street }}</span>
          <span>&nbsp;</span>
          <span v-if="postNumber" class="dotColor"> • </span>
          <span>&nbsp;</span>
          <span v-if="postNumber" class="instance">{{ postNumber }}</span>
          <span>&nbsp;</span>
          <span v-if="city" class="instance">{{ city }}</span>
        </div>
        &nbsp;<span style="color: #FFC1B4"></span>&nbsp;
         </div>

    <div class="form">
      <div class="form-group">
        <div class="label guideFont">
          <label for="formGroupExampleInput">Name:</label>
        </div>
        <input type="text" v-model="name" v-on:keyup="setName" class="form-control" id="formGroupExampleInput" placeholder="Firstname Lastname">
      </div>
      <div class="form-group">
        <div class="label guideFont">
          <label for="formGroupExampleInput2">Work title:</label>
        </div>
        <input type="text" v-model="titel" v-on:keyup="setTitel" class="form-control" id="" placeholder="Title">
      </div>
      <div class="form-group">
        <div class="label">
           <label for="formGroupExampleInput">Business area:</label>
        </div>
        <input type="text" v-model="businessArea" class="form-control" v-on:keyup="setBusinessArea" id="formGroupExampleInput" placeholder="Business Area">
      </div>
      <div class="form-group">
        <div class="label guideFont">
           <label for="formGroupExampleInput">Phone number:</label>
        </div>
        <input type="text" v-model="phone" class="form-control" id="formGroupExampleInput" v-on:keyup="setPhone" placeholder="+46 525 XX XX XX">
      </div>
      <div class="form-group">
        <div class="label guideFont">
           <label for="formGroupExampleInput">HomePage:</label>
        </div>
        <input v-model="homepage" type="text" class="form-control" id="formGroupExampleInput" v-on:keyup="setHomepage" placeholder="www.linderoths.se">
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
        <input v-model="local" type="text" class="form-control" id="formGroupExampleInput" v-on:keyup="setLocal" placeholder="Location">
      </div>
      <div class="form-group">
        <div class="label guideFont">
           <label for="formGroupExampleInput">Street:</label>
        </div>
        <input v-model="street" type="text" class="form-control" id="formGroupExampleInput" v-on:keyup="setStreet" placeholder="Street">
      </div>
      <div class="form-group">
        <div class="label guideFont">
             <label for="formGroupExampleInput">Post number:</label>
        </div>
        <input v-model="postNumber" type="text" class="form-control" id="formGroupExampleInput" v-on:keyup="setPostNumber" placeholder="Post Number">
      </div>
      <div class="form-group">
        <div class="label guideFont">
            <label for="formGroupExampleInput">City:</label>
        </div>
        <input v-model="city" type="text" class="form-control" id="formGroupExampleInput" v-on:keyup="setCity" placeholder="City">
      </div>
    </div>
    <div class="card guideFont">
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
      name: localStorage.getItem('mail-signature_name') ? localStorage.getItem('mail-signature_name') : '',
      titel: localStorage.getItem('mail-signature_titel') ? localStorage.getItem('mail-signature_titel') : '',
      businessArea: localStorage.getItem('mail-signature_businessArea') ? localStorage.getItem('mail-signature_businessArea') : '',
      phone: localStorage.getItem('mail-signature_phone') ? localStorage.getItem('mail-signature_phone') : '',
      homepage: localStorage.getItem('mail-signature_homepage') ? localStorage.getItem('mail-signature_homepage') : '',
      social: localStorage.getItem('mail-signature_social') ? localStorage.getItem('mail-signature_social') : '',
      local: localStorage.getItem('mail-signature_local') ? localStorage.getItem('mail-signature_local') : '',
      street: localStorage.getItem('mail-signature_street') ? localStorage.getItem('mail-signature_street') : '',
      postNumber: localStorage.getItem('mail-signature_post') ? localStorage.getItem('mail-signature_post') : '',
      city: localStorage.getItem('mail-signature_city') ? localStorage.getItem('mail-signature_city') : ''
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
      localStorage.setItem('mail-signature_phone', this.phone)
    },
    setHomepage () {
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
