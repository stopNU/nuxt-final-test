<template>
  <div class="contact-form">
    <h4>{{title}}</h4>
    <div id="form"></div>
  </div>
</template>

<script>
export default {
  props: {
      formId: String,
      title: String
  },
  mounted(){
    const script = document.createElement('script');
    script.src = 'https://js.hsforms.net/forms/v2.js';
    document.body.appendChild(script);
    
    script.addEventListener('load', () => {
        
    	if(window.hbspt) {
      	window.hbspt.forms.create({
            portalId: '446773',
            formId: this.formId,
            target: '#form'
        })
      }
    });

  }
}
</script>

<style scoped lang="scss"> 
    h4{
        color: $color-brand-dark;
        margin-bottom: 1.5rem;
    }
</style>