<template>
    <div class="font-sans bg-grey-lighter flex flex-col min-h-screen w-full">
      <div class="flex-grow container mx-auto sm:px-4 pt-6 ">
        <div class="bg-white border-t border-b sm:border-l sm:border-r sm:rounded shadow mb-6">
          <div class="hidden lg:flex">
            <div class="w-1/2 text-center py-8">
                  <!-- This is an example component -->
              <div class="pt-2 relative mx-auto text-gray-600">
                <input class="border-2 border-gray-300 bg-white h-10 px-5 pr-16 rounded-lg text-sm focus:outline-none"
                  type="text" name="search" id="search" placeholder="search..." v-model="search">
        
              </div>
            </div>
          </div>
        </div>

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
			<input type='button' class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded mt-5" @click='printValues()' value='Print Selected Item'>

		</div>

     <div class="flex flex-wrap mt-5 mx-4">
      <div class="w-full mb-6 lg:mb-0  px-4 flex flex-col">
        <div class="flex-grow flex flex-col bg-white border-t border-b sm:rounded sm:border shadow overflow-hidden">
          <div class="border-b bg-gray-300">
            <div class="flex justify-between px-6 mb-px">
              <h3 class=" py-4 font-bold text-lg">Selected items </h3>
              <div class="flex">
              </div>
            </div>
          </div>
          <!-- start -->
          <div class="flex-grow flex px-6 py-6 text-grey-darker items-center border-b -mx-4">
            <div class="w-2/5 xl:w-1/4 px-4 flex items-center">
              <span class="text-lg">{{selectedlang}}</span>
            </div>
          </div>
          <!-- end -->
        </div>
      </div>
    </div>

    <div class="flex flex-wrap mt-6 mx-4">
      <div class="w-full mb-6 lg:mb-0  px-4 flex flex-col">
        <div class="flex-grow flex flex-col bg-white border-t border-b sm:rounded sm:border shadow overflow-hidden">
          <div class="border-b bg-gray-300">
            <div class="flex justify-between px-6 mb-px">
              <h3 class=" py-4 font-bold text-lg">ITEM</h3>
              <div class="flex">
              </div>
            </div>
          </div>
          <!-- start -->
          <div v-for="(lang, index) in filteredLanguage" :key="index" class="flex-grow flex px-6 py-6 text-grey-darker items-center border-b -mx-4">
            <div class="w-2/5 xl:w-1/4 px-4 flex items-center">
              <span class="text-lg">{{lang}}</span>
            </div>
          </div>
          <!-- end -->
        </div>
      </div>
    </div>

      </div>
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
        langsdata: ["Inggris","Prancis","Italia","Arab","Indonesia","Malaysia"],
        languages: [],
        selectedlang: "",
        search: ""
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
              this.langsdata.splice(key, 1);
          }
      },
     
  },
    computed: {
    filteredLanguage: function() {
      return this.langsdata.filter((lang) => {
          return lang.match(this.search);
      });
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
