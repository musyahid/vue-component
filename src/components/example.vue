<template>			
		<div id='myapp'>
			
			<!-- Check All -->
			<input type='checkbox' @click='checkAll()' v-model='isCheckAll'> Check All

			<!-- Checkboxes list -->
			<ul>
				<li v-for="lang of langsdata" :key="lang.id">
					<input type='checkbox' v-bind:value='lang' v-model='languages' @change='updateCheckall()'>{{ lang }}
				</li>
			</ul>

			<!-- Print -->
			<input type='button' @click='printValues()' value='Print Selected Values'>

			<br>
			Selected items : {{ selectedlang }}

		</div>
</template>

<script>

export default {
  name: 'SearchBox',
  props: {
    msg: String
  },
    data() {
    return {
        isCheckAll: false,
        langsdata: ["PHP","Vue.js","AngularJS","jQuery","JavaScript"],
        languages: [],
        selectedlang: ""
    }
  },
            methods: {
            checkAll: function(){

                this.isCheckAll = !this.isCheckAll;
                this.languages = [];
                if(this.isCheckAll){	// Check all
                    for (var key in this.langsdata) {
                        this.languages.push(this.langsdata[key]);
                    }
                }

            },
            updateCheckall: function(){
                if(this.languages.length == this.langsdata.length){
                    this.isCheckAll = true;
                }else{
                    this.isCheckAll = false;
                }
            },
            printValues: function(){
                this.selectedlang = "";
                // Read Checked checkboxes value
                for (var key in this.languages) {
                    this.selectedlang += this.languages[key]+", ";  
                }
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
