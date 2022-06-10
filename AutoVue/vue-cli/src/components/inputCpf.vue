<template>
  <div>
    
    <input type='text' maxlength= "14" id='cpfInput' placeholder='000.000.000-00' v-model="formatat" @input="cpfChange">
     <p id="alert">Please type in numbers only</p> 
      <div id="formatat">
          <p>Numar formatat: {{ formatat }}</p>
          <p id="format"></p>
      </div>
    <div id="neformatat">
      <p>Numar neformatat: </p>
      <p id="unformat">{{ neformatat }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      formatat: "",
      neformatat: ""
    }
  },
  methods: {
      cpfChange(){
        this.neformatat = this.formatat.replace(/[^0-9]+/g, '')
        console.log(this.formatat)

        const cpfLength = this.neformatat.length;

        const partOne = this.neformatat.slice(0, 3) + ".";
        const partTwo = this.neformatat.slice(3, 6) + ".";
        const partThree = this.neformatat.slice(6, 9) + "-";

        if(cpfLength < 4) this.formatat = this.neformatat;
        else if (cpfLength >= 4 && cpfLength < 7) this.formatat = partOne + this.neformatat.slice(3);
        else if (cpfLength >= 7 && cpfLength < 10) this.formatat = partOne + partTwo + this.neformatat.slice(6);
        else if (cpfLength >= 10 && cpfLength < 12) this.formatat = partOne + partTwo  + partThree + this.neformatat.slice(9);
      }
  }

}
</script>

<style>
input {
    display: block;
    padding: 8px 16px;
    font-size: 2em;
    margin: 10px auto;
    width: 50%;
    box-sizing: border-box;
    border-radius: 10px;
    border: 3px solid #ccc;
    outline: none !important;
    margin-top: 300px;
  }

  input.invalid {
    border: 3px solid orangered;
  }
  p{
    text-align: center;
    font-size: 30px;
  }
  #neformatat{
    display: flex;
    justify-content: center;
  }
  #formatat{
    display: flex;
    justify-content: center;
  }
  #alert{
      font-size: 13px;
      color: gray;
  }
</style>
