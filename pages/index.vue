<template>
  <div class="container">
    <!-- Filtrage section -->
    <div class="Sectionfilt">
      <div class="Section">
        <div class="filter-column">
          <p class="underlineRed">RECIPE TYPE</p>
 <div class="checkbox" v-for="type in allTypes" :key="type">
  <input
    type="checkbox"
    :value="type"
    :checked="selectedTypes.includes(type)"
    @change="toggleType(type)"
    class="chek"
    :id="'checkbox-' + type"
  />
  <label :for="'checkbox-' + type">{{ type }}</label>
</div>
      
        </div>
      </div>

      <div class="rf_other">
        <div class="filter-column">
       
<!-- Nutritional-->
      <div class="rf_other">
				<span class="rf_title1">Nutritional</span>
        <ul id="rf_other_ul">
    <!-- Calories -->
              <li class="cul1">
                <span class="rf_adv_t2">
                  <label for="calories_operation">Calories:</label>
                </span>
                <span class="rf_select_w">
                  <select class="rf_other_select" id="calories_operation" name="calories_operation" v-model="selectedNutritionRange" @change="filterProducts">
                    <option value="">Any Calories</option>
                    <option value="0-50">Under 50</option>
                    <option value="0-100">Under 100</option>
                    <option value="0-150">Under 150</option>
                    <option value="0-200">Under 200</option>
                    <option value="0-250">Under 250</option>
                  </select>
                </span>
              </li>
              <!-- End Calories -->
        
<!-- Protein-->
        <li class="cul2"><span class="rf_adv_t2"><label for="protein_operation">Protein:</label></span>
                        <span class="rf_select_w">
              <select class="rf_other_select" id="protein_operation" name="protein_operation" v-model="selectedProteinRange" @change="filterProducts">
            <option value="" selected>Any Protein</option>
            <option value="10-50">Over 10g</option>
            <option value="20-50">Over 20g</option>
            <option value="30-50">Over 30g</option>
            <option value="40-50">Over 40g</option>
            <option value="50-100">Over 50g</option>
          </select>
                        
                        </span>
                        </li>
       <!-- End Protein-->
       <!-- Carbs-->
       <li class="cul1"><span class="rf_adv_t2"><label for="carbs_operation">Carbs:</label></span>
                        <span class="rf_select_w">
                       <select class="rf_other_select" id="carbs_operation" name="carbs_operation" v-model="selectedCarbsRange" @change="filterProducts">
                            <option value=""  selected>Any</option>
                            <option value="0-50" >Under 50 g</option>
                            <option value="0-100" >Under 100 g</option>
                            <option value="0-150" >Under 150 g</option>
                            <option value="0-200" >Under 200 g</option>
                            <option value="0-250" >Under 250 g</option>
                            <option value="0-300" >Under 300 g</option>
                            <option value="0-350" >Under 350 g</option>
                            <option value="0-400" >Under 400 g</option>
                            <option value="0-450" >Under 450 g</option>
                            <option value="0-500" >Under 500 g</option>
                            <option value="0-550" >Under 550 g</option>
                            <option value="0-600" >Under 600 g</option>
                            <option value="0-650" >Under 650 g</option>
                            <option value="0-700" >Under 700 g</option>
                            <option value="0-750" >Under 750 g</option>
                        </select>
                        </span>
                        </li>
       <!-- End Carbs-->
        <!--  Fiber-->
         <li class="cul2"><span class="rf_adv_t2"><label for="fiber_operation">Fiber:</label></span>
                        <span class="rf_select_w">
                        <select class="rf_other_select" id="carbs_operation" name="carbs_operation" v-model="selectedFiberRange" @change="filterProducts">
                             <option value=""  selected>Any</option>
                            <option value="10-50" >Over 10 g</option>
                            <option value="20-50" >Over 20 g</option>
                            <option value="30-50" >Over 30 g</option>
                            <option value="40-50">Over 40 g</option>
                            <option value="50-100" >Over 50 g</option>
                        </select>
                        </span>
                        </li>
         <!-- End Fiber-->
         <!-- Fat-->
         <li class="cul2"><span class="rf_adv_t2"><label for="protein_operation">Fat:</label></span>
                        <span class="rf_select_w">
                       <select class="rf_other_select" id="fat_operation" name="fat_operation" v-model="selectedFatRange" @change="filterProducts">
                            <option value=""  selected>Any</option>
                            <option value="10-50" >Over 10 g</option>
                            <option value="20-50" >Over 20 g</option>
                            <option value="30-50" >Over 30 g</option>
                            <option value="40-50" >Over 40 g</option>
                            <option value="50-100" >Over 50 g</option>
                        </select>
                        </span>
                        </li>

         <!-- End Fat-->
           <!--  Dietary-->
           <li class="cul1"><span class="rf_adv_t2"><label for="dietary">Dietary:</label></span>
                        <span class="rf_select_w">
                        <select class="rf_other_select" id="dietary" name="dietary" v-model="selectedDietaryRange" @change="filterProducts">
                            <option value="" selected="">Any</option>
                            <option value="Diat1">Vegetarian</option>
                            <option value="Diat2">Vegan</option>
                            <option value="Diat3">Lactose Free</option>
                            <option value="Diat4">Gluten Free</option>
                            <option value="Diat5">Low Fat</option>
                            <option value="Diat2">Low Carb</option>
                            <option value="Diat3">Sugar Free</option>
                        </select>
                        </span>
                        </li>
            <!--  End Dietary-->
              
              
				</ul>
            </div><!--rf_other-->

        </div>
      </div>
      <!--End Nutritional-->  
       <!--Minutes--> 
        <div class="rf_minutes">
				<span class="rf_title1">Minutes</span>
				<ul id="rf_min_ul">
					<li class="cul1"><label class="cul1label" for="prep_time">Prep: </label>
                       <select class="rf_other_select" id="calories_operation" name="calories_operation" v-model="selectedPrepRange"  @change="filterProducts">
                            <option value=""  selected>Any</option>
                            <option value="5-60" >Under 5</option>
                            <option value="10-60" >Under 10</option>
                            <option value="15-60" >Under 15</option>
                            <option value="20-60" >Under 20</option>
                            <option value="25-60" >Under 25</option>
                            <option value="30-60" >Under 30</option>
                            <option value="35-60" >Under 35</option>
                            <option value="40-60" >Under 40</option>
                            <option value="45-60" >Under 45</option>
                            <option value="50-60" >Under 50</option>
                            <option value="55-60" >Under 55</option>
                            <option value="60-100" >Under 60</option>
                        </select>
                        
					</li>
					<li class="cul1"><label class="cul1label" for="total_time">Total:</label> <span class="rf_select_w">
          <select class="rf_time_select" id="total_time" name="total_time" v-model="selectedTotalRange"  @change="filterProducts">
                            <option value=""  selected>Any</option>
                            <option value="0-5" >Under 5</option>
                            <option value="0-10" >Under 10</option>
                            <option value="0-15" >Under 15</option>
                            <option value="0-20" >Under 20</option>
                            <option value="0-25" >Under 25</option>
                            <option value="0-30" >Under 30</option>
                            <option value="0-35" >Under 35</option>
                            <option value="0-50" >Under 40</option>
                            <option value="0-45" >Under 45</option>
                            <option value="0-50" >Under 50</option>
                            <option value="0-55" >Under 55</option>
                            <option value="0-60" >Under 60</option>
                            <option value="0-65" >Under 65</option>
                            <option value="0-70" >Under 70</option>
                            <option value="0-75" >Under 75</option>
                        </select>
                        </span>
                    </li>

				</ul>
        <!--rf_minutes-->
				<div style="clear:left;"></div>
			</div><!--End rf_minutes-->
        <!--END Minutes--> 

    </div>   
    <!--  Filtrage section -->
    <div id="recipe_finder_top" class="page_width_limit">
    
		<div class="rf_results_top">
  	
			<span name="recipe_finder_results_label" id="recipe_finder_results_label" class="rf_results_title"><h1>Healthy Recipe Results</h1></span>	
		</div>
        
 </div> 
   <!-- <div v-if="loading" class="loading">Loading...</div>-->
 <div class="grid-container">

   <!-- <div  v-for="p in filteredProducts"
        :key="p.id" class="grid-item">  -->
        
        <div v-for="(p, index) in paginatedProducts" :key="p.id" class="grid-item">
         
        <div id="finder_results">
        <div id="hom16_w">
	<div id="hom16" class="page_width_limit">
<div class="bg r2">
<div class="pic_w">
						<a href="#">
						<img :src="p.image" border="0" class="pic" alt="image">

							</a>
				
                        <div class="pic_overlay">
                            <div class="round_time"><span class="round_t1">TIME</span><span class="round_t2">{{p.time}}</span></div>
                            <div class="round_cals"><span class="round_t1">CALS</span><span class="round_t2">{{p.calories}}</span></div>
                        </div>
                        
                    </div>
                    <div class="rtext">						
                        <a href="#" class="item">{{ p.name }}</a>
                        <p class="text">
                        
                        This is my own creation.  Sweet, mild, healthy, non-fishy tilapia is complimented by lemon, capers, butter, broth, and white wine in this satisfying and deceptively easy meal.  I like my piccata lemony with touches of onion, garlic, and capers to round out the taste.  This is a basic recipe for 1 lb. of filets.  Please reduce this recipe accordingly if you use fewer filets, unless you want the leftunders as lunch or another dinner, like I do, if all is not eaten during the first go-‘round.  I am a strong believer in flexibility, so experiment and substitute most any flaky white fish, pounded-flat veal or chicken cutlets, according to your creativity, pantry contents, budget, ingredient-availability, and personal tastes.  I would greatly appreciate your feedback on this recipe, including any suggestions, comments, and input.  Thank you for reading and trying this recipe!  SparkPeople rocks my world!<span class="by">Submitted by: <a href="more-about-me.asp?user=4203456" rel="nofollow">KEEPITMOVING</a></span>
                        </p>

				
						<div class="nutrients">
						<span class="ncals">CALORIES <b>{{p.calories}}</b> </span>
						<span class="nfat">FAT <b>{{p.fat}}</b></span>
						<span class="nprotein">PROTEIN <b>{{p.protein}}</b></span>
						<span class="ncarbs">CARBS <b>{{p.carbs}}</b></span>
						<span class="nfiber">FIBER <b>{{p.fiber}}</b></span>
						</div>					
						<div class="clear1"></div>
                </div><!--rtext-->

 </div>
 </div>
 </div>
 
 </div>
 
 </div>

 </div>
<div class="pagination-buttons">
    <button v-if="currentPage > 1" @click="previousPage">‹ Previous Recipes</button>
    <button v-if="currentPage < totalPages" @click="nextPage">Show More Healthy Recipes ›</button>
  </div>

 <!--  End Filtrage section -->
<div class="showAllProducts" v-if="hasProducts">
</div>
<div class="text"  v-else>
  NO PRODUCT SELECTED
</div>
</div>
  
</template>


<script>
import data from "../database.json";

export default {
  data() {
    return {
      filteredProducts: [],
      selectedNutritionRange: "",
      selectedProteinRange: "",
      selectedCarbsRange: "",
      selectedFiberRange: "",
      selectedFatRange: "",
      selectedPrepRange: "",
      selectedTotalRange: "",
      selectedDietaryRange:"",
      selectedTypes: [],
      showAllProducts: false,
      currentPage: 1,
      perPage: 2,
 
    };
  },
  mounted() {
    this.filteredProducts = data.product;
    // Récupérer tous les types disponibles
  const types = new Set();
  this.filteredProducts.forEach((product) => {
    types.add(product.type);
  });

  this.allTypes = Array.from(types);
  },
  computed: {
    totalPages() {
      return Math.ceil(this.filteredProducts.length / this.perPage);
    },
    uniqueTypes() {
      const types = new Set();
      this.filteredProducts.forEach((product) => {
        types.add(product.type);
      });
      return Array.from(types);
    },
     hasProducts() {
      return this.filteredProducts.length > 0;
    },
    paginatedProducts() {
      const startIndex = (this.currentPage - 1) * this.perPage;
      const endIndex = startIndex + this.perPage;
      return this.filteredProducts.slice(startIndex, endIndex);
    },
  },
  methods: {
       previousPage() {
      this.currentPage--;
    },
    nextPage() {
      this.currentPage++;
    },
toggleType(type) {
  // Vérifier si le type est déjà sélectionné
  const index = this.selectedTypes.indexOf(type);
  if (index > -1) {
    this.selectedTypes.splice(index, 1); // Désélectionner le type
  } else {
    this.selectedTypes.push(type); // Sélectionner le type
  }

  this.filterProducts();
},
   filterProducts() {
  const {
    selectedNutritionRange,
    selectedProteinRange,
    selectedCarbsRange,
    selectedFiberRange,
    selectedFatRange,
    selectedDietaryRange,
    selectedPrepRange,
    selectedTotalRange,
    selectedTypes,
  } = this;

  this.filteredProducts = data.product.filter((product) => {
    // Filtrer par plage de nutrition
    if (selectedNutritionRange !== "") {
      const [minCalories, maxCalories] = selectedNutritionRange.split("-");
      const calories = parseInt(product.calories);
      if (
        calories < parseInt(minCalories) ||
        calories > parseInt(maxCalories)
      ) {
        return false;
      }
    }

    // Filtrer par plage de protéines
    if (selectedProteinRange !== "") {
      const [minProtein, maxProtein] = selectedProteinRange.split("-");
      const protein = parseInt(product.protein);
      if (
        protein < parseInt(minProtein) ||
        protein > parseInt(maxProtein)
      ) {
        return false;
      }
    }

    // Filtrer par plage de glucides
    if (selectedCarbsRange !== "") {
      const [minCarbs, maxCarbs] = selectedCarbsRange.split("-");
      const carbs = parseInt(product.carbs);
      if (carbs < parseInt(minCarbs) || carbs > parseInt(maxCarbs)) {
        return false;
      }
    }

    // Filtrer par plage de fibres
    if (selectedFiberRange !== "") {
      const [minFiber, maxFiber] = selectedFiberRange.split("-");
      const fiber = parseInt(product.fiber);
      if (fiber < parseInt(minFiber) || fiber > parseInt(maxFiber)) {
        return false;
      }
    }

    // Filtrer par plage de matières grasses
    if (selectedFatRange !== "") {
      const [minFat, maxFat] = selectedFatRange.split("-");
      const fat = parseInt(product.fat);
      if (fat < parseInt(minFat) || fat > parseInt(maxFat)) {
        return false;
      }
    }
    //Filter Dietary
     // Filtrer par régime alimentaire
    if (selectedDietaryRange !== "") {
      const dietary = selectedDietaryRange;
      if (product.Diat !== dietary) {
        return false;
      }
    }

    // Filtrer par plage de temps de préparation
    if (selectedPrepRange !== "") {
      const [minPrep, maxPrep] = selectedPrepRange.split("-");
      const prepTime = parseInt(product.prepare);
      if (prepTime < parseInt(minPrep) || prepTime > parseInt(maxPrep)) {
        return false;
      }
    }

    // Filtrer par plage de temps total
    if (selectedTotalRange !== "") {
      const [minTotal, maxTotal] = selectedTotalRange.split("-");
      const totalTime = parseInt(product.time);
      if (totalTime < parseInt(minTotal) || totalTime > parseInt(maxTotal)) {
        return false;
      }
    }

    // Filtrer par types sélectionnés
      if (selectedTypes.length > 0) {
      // Si aucun type sélectionné ne correspond au type du produit, le filtrage échoue
      if (!selectedTypes.includes(product.type)) {
        return false;
      }
    }
   

    return true;
  });

   
}
  },
};
</script>

<style >
.grid-container {
  display: grid;
  gap: 0px;
  grid-template-columns: auto auto auto;
  padding: 10px;
}
@media screen and (max-width: 966px ) and (min-width:  576px){
.grid-container {
  display:block;
  gap: 0px;
  grid-template-columns: auto auto auto;
  padding: 10px;
}  
}
.grid-item {
  background-color: rgba(255, 255, 255, 0.8);
  padding: 20px;
  font-size: 30px;
  text-align: center;
  width:30px
}
	#rf_type_ul {list-style:none; margin:0; padding:0; text-align:left;}
	#rf_type_ul LI {float:left; font-size:13px; text-align:left;  padding:1px .5%;  }
	#rf_type_ul LI LABEL {}
	#rf_type_ul LI.cul1 {width:39%;}
	#rf_type_ul LI.cul2 {width:59%;}
	
	#rf_other_ul {list-style:none; margin:0; padding:0; text-align:left;color:white}
	#rf_other_ul LI {float:left; font-size:13px; text-align:left;  padding:3px 0; }
	#rf_other_ul LI.cul1 {width:49%;}
	#rf_other_ul LI.cul2 {width:49%;}
  .rf_results_title {font-size:20px; text-transform:uppercase; 
  color:#666666; display:inline-block;
  font-weight:400; letter-spacing:1px;}
  #hom16_w { margin-top:15px;
  padding: 10px;  
  }
  #rf_min_ul {list-style:none; margin:0 0 0 0; padding:0; text-align:left;}
  #rf_min_ul LI {float:left; font-size:13px; text-align:left; padding:4px .5%; }
	#rf_min_ul LI.cul1 {margin-left:0;}
  #rf_min_ul LI LABEL.cul1label{
    color:white
  }
  
	#hom16_w .sponsored {float:right; margin:6px;}
	#hom16_w .r2 { 
    background-color:white;
     border:1px solid #d7d7f9;
     box-shadow:0px 0px 5px #DADADA; 
     border-radius:4px; text-align:center;
      max-width:300px; min-width:300px; 
      position:relative; 
      margin-bottom:15px;}
	#hom16_w .r1{ }
	#hom16_w .r2{}
	#hom16_w .item {font-size:17px; 
  font-weight:400;
   margin:15px auto 60px auto; display:block; text-decoration:none;}
	#hom16_w a.item {color:black; text-decoration:none;  display:block; padding-top:30px}
	
	#hom16_w .rtext {width:96%; margin-left:auto; margin-right:auto; padding-bottom:5px;}
	#hom16_w P {padding:6px 0 6px 0; margin:0; font-size:11px; display:none;}
	#hom16_w .by {font-size:13px; font-style:normal; color:#94a531; display:block; margin: 6px 0 0 0; display:none;}
	#hom16_w .by A {font-size:13px; font-style:normal; color:#848429; text-decoration:underline;  text-transform:uppercase;}
	
	#hom16_w .pic_w {  margin: 0px 2% 0px 0px; width:100%; text-align:center; position:relative;}
	#hom16_w .pic { border:0; width:100%; max-width:100%; margin-right:auto; /*transition: all .8s ease-in-out; */ }
	
	
	#hom16_w .ratings { margin:6px 0;   text-align:left; }
	#hom16_w .ratings SPAN{ font-size:11px;  text-align:left;  display:inline-block; vertical-align:middle;}
	#hom16_w .ratings_num {margin-left:5px; color:#ff7b08;}
	#hom16_w .nutrients { clear:both; margin:0px; height:50px; padding-top:5px; font-size:10px;  color:#555; background-color:#fafafa; box-shadow: inset -1px 2px 3px rgba(0,0,0,.1); position:absolute; bottom:0; left:0; width:300px;}
	#hom16_w .nutrients A {color:#555;}
	
	#hom16_w .grayline {color:#ccc;}
	#hom16_w .clear1 {clear:both;}
	#hom16_w .clear2 {clear:both;}
		
	#hom16_w .ncals, #hom16_w .nfat,  #hom16_w .nprotein ,#hom16_w .ncarbs, #hom16_w .nfiber  { width:22%; border-right:1px solid #f2f2f2; display:inline-block; text-align:center;}
	#hom16_w .nfiber {border-right:0;}
	
	#hom16_w .ncals B:after, #hom16_w .nfat B:after, #hom16_w .nprotein B:after, #hom16_w .ncarbs B:after, #hom16_w .nfiber B:after  { content:" g"; font-size:10px; font-family:Georgia, "Times New Roman", Times, serif;}
	
	#hom16_w .nutrients B {font-size:20px; display:block; font-weight:400;}
	#hom16_w .ncals {color:#555; display:none;}
	#hom16_w .nfat {color:#555;}
	#hom16_w .nprotein {color:#555;}
	#hom16_w .ncarbs {color:#555;}
	#hom16_w .nfiber {color:#555;}
	
	#hom16_w .pic_overlay{position:absolute; right:0px; bottom:-25px; z-index:2; }
	#hom16_w .round_time {float:right;  background-color:#207D88; width:54px; height:54px; border-radius:54px; overflow:hidden; box-shadow:1px 2px 3px rgba(0,0,0,.2); }
	#hom16_w .round_cals {float:right;  background-color:#009F9F; width:54px; height:54px; border-radius:54px; overflow:hidden; box-shadow:1px 2px 3px rgba(0,0,0,.2); }
	#hom16_w .round_t1 {font-size:11px; line-height:11px; font-weight:700; display:block; text-align:center; color:white; margin-top:7px;}
	#hom16_w .round_t2 {font-size:20px; line-height:24px; font-weight:400; display:block; text-align:center; color:white;}

.container {
margin: 0 auto;
width:100%;
position: relative;
width:1250px
  
}
.checkbox{
  color:white;
  font-size: 13px;
  text-align: left;
  font-weight:700;
  padding-left:20;
}
input[type="checkbox" i] {
  background:red !important;
  width:20px;
  margin: 3px 3px 3px 4px;
}
.Section {
    float: left;
    width: 24%;
    padding: 0 0 0 2%;
    min-height: 150px;
    
}
.rf_other_select {
    border: 1px solid #22A7EE;
    padding: 3px 3px;
    font-size: 13px;
    width: 106px;
    border-radius: 3px;
    background: #fff;
}

.rf_other{
    float: left;
    width: 60%;
    padding: 0 0 0 3%;
    min-height: 150px;
    text-align: center;
    margin-bottom:20px;
}
.rf_adv_t2{width:50px; display:inline-block;
 text-align:right; vertical-align:middle}
.rf_title1 {
    color:white;
    text-transform: uppercase;
    font-size: 13px;
    font-weight: 600;
    display: inline-block;
    padding-top: 10px;
    margin-bottom: 8px;
    text-align: center;
    padding-bottom: 1px;
   border-bottom: 2px solid #C92921; 
    margin-left: auto;
    margin-right: auto;
}

.rf_other_ul{
  list-style:none;
  margin:0; padding:0;
 
 
}
.Sectionfilt {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
 background:url(https://sparkpeo.hs.llnwd.net/e5/images/home_finder_bg.jpg) ;
 background-size:cover; background-color:#593E2F;
 margin-bottom:20px
}

.filter-column {
  display: flex;
  flex-direction: column;
}

.underlineRed {
color: #fff;
    text-transform: uppercase;
    font-size: 13px;
    font-weight: 600;
    display: inline-block;
    padding-top: 10px;
    margin-bottom: 8px;
    text-align: center;
    padding-bottom: 1px;
    border-bottom: 2px solid #C92921;
    margin-left: auto;
    margin-right: auto;  color: white;
  margin-bottom: 10px;
}

.produkts {
  margin-top: 20px;
  padding: 10px;
  border: 1px solid #ccc;
  margin-bottom: 15px;
  display:flex;
  
}

.product-name {
  font-weight: bold;
}

.product-price {
  color: green;
}

.product-protein {
  color: blue;
}
.pagination-buttons {
  text-align: center;
  margin-bottom:30px

}
.pagination-buttons button{
   border: none;
 width:50%;
  font-weight: 400;
  font-family: 'Open Sans', 'Helvetica Neue', Arial, sans-serif;
  width: 30%;
  text-align: center;
  margin-left: 2%;
  margin-right: 2%;
  background: #ff7b08;
  border: 0;
  color:white;
  margin-bottom: 30px;
  padding-top:15px;
  padding-bottom:15px;
  border-radius:20px


}
.text{
 display: flex;
  justify-content: center;
  align-items: center;
  color: red;
  font-size: 50px;
   font-weight: bold;

}
.chek{
  background:red
}

</style>