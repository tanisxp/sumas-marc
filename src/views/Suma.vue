<template>
  <v-container grid-list-md text-xs-center>
    <v-layout text-center wrap>

      <v-flex xs12>
        <h1 class="display-2 font-weight-bold mb-3">Sumas para Marc </h1>
        <p class="subheading font-weight-regular">
          De cero a superguerrero...    
        </p>
        <div style="border:1px solid; height:60px">
          <div ref="div_record" class="subheading font-weight-regular" style="display:block;">
            Record de  <span style="font-size:40px">{{record}} </span> segundos!!
          </div>
        </div>
      </v-flex>

    <v-flex  xs3 style="border:1px solid">

    </v-flex>

    <v-flex  xs3 style="border:1px solid">
    </v-flex>

    <v-flex  xs3 style="border:1px solid">

      <v-flex  xs10 style="border:1px solid red">
          <v-card max-width="100" max-height="100" class="mx-auto" color="#385F73" dark>
                    <v-card-text class="white--text">
                      <div class="headline mb-2">{{num1}}</div>
                    </v-card-text>
          </v-card>
      </v-flex>
       
      <v-flex  xs10 style="border:1px solid red">
          <v-card max-width="100" max-height="100" class="mx-auto" color="#385F73" dark>
                    <v-card-text class="white--text">
                      <div class="headline mb-2">{{num2}}</div>
                    </v-card-text>
          </v-card>
      </v-flex>

      <v-flex  xs10 style="border:1px solid red">
          <v-card max-width="100" max-height="80" class="mx-auto" color="#cccccc">
                    <v-text-field
                      v-model="guess"
                      autofocus
                      full-width
                      color="#ffffff"
                      @keyup.native.enter="sum_on()"
                    ></v-text-field>
          </v-card>
      </v-flex>

    </v-flex>

    <v-flex  xs3 style="border:1px solid">
    </v-flex>


     
    </v-layout>
  </v-container>
</template>


<script>
export default {  
  data() {
    return {
      num1: Math.round(Math.random() * 10, 2),
      num2: Math.round(Math.random() * 10, 2),
      total: 0,
      guess: "",
      segundos : 0,
      record: 0,
      start: new Date(),
      end: new Date(),
      record : this.readCookie('record_cookie')  
    };
  },
  methods: {
    sum() {
      this.total = this.num1 + this.num2;
      this.end = new Date() - this.start;
      if (this.guess == this.total) {
        this.segundos =  Math.floor(this.end / 1000);
        this.cookie_value = parseInt(this.readCookie('record_cookie'));
        if(this.segundos < this.cookie_value) {
          document.cookie = "record_cookie=" + this.segundos;        
          this.$refs["div_record"].style = 'display:block';
        } 
      } else {
        alert("NOOOOOOOOOOO");
      }
       this.record = this.readCookie('record_cookie')  ;

        setTimeout(function() {
         window.location.reload();
        }, 2000);
     
    },
    readCookie(name) {
        var nameEQ = name + "=";
        var ca = document.cookie.split(';');
        for(var i=0;i < ca.length;i++) {
            var c = ca[i];
            while (c.charAt(0)==' ') c = c.substring(1,c.length);
            if (c.indexOf(nameEQ) == 0) return c.substring(nameEQ.length,c.length);
        }
        return null;
    },
    sum_on() {
      this.sum();
    }
  }
};
</script>