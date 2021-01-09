<html>
<p>
  Add links to <a href="links.json">JSON file</a>. <br>
  JSON file restrictions: 1 title, 1 url, 1+ tags/categories. Categories must be lowercase to sort correctly.<br>
  Change "jsonsite" variable in README file to applicable json file.
</p>

<a href="#" onclick="alllinks()">All Favorites</a>
<br>
<a href="#" onclick="catlinks()">Categories</a>

<br><br>
<p id="links"></p>

<script>
/*Site that stores JSON file*/
var jsonsite="https://gist.githubusercontent.com/david-krause/f4d558c72f47a0e475ffad233fdfb800/raw/a227e460274fce832508e859d8887b44346abb2e/links.json";
/*var jsonsite="links.json";*/
/******/

/****ALL LINKS FUNCTION****/
function alllinks(){

var jsnhttp = new XMLHttpRequest();
/*perform this function one page is loaded*/
jsnhttp.onreadystatechange = function() {
  if (this.status == 200 && this.readyState == 4) {
    var i, n, lnks=[], jsnObj = JSON.parse(this.responseText);
    for(i in jsnObj){
    	lnks.push("<a id=" + jsnObj[i].title + " target='_blank' href=" + jsnObj[i].url + ">" + jsnObj[i].title + "</a><br>")
      }
    }
     /*lnks variable is set to the HTML paragraph*/
	/*join method to remove commas*/
    document.getElementById("links").innerHTML = lnks.sort().join("");
	};
/*call site to get JSON data*/
jsnhttp.open("GET", jsonsite,true);
jsnhttp.send();
}
/****END OF ALL LINKS FUNCTION****/


/*****LINKS BY CATEGORY FUNCTION*****/
function catlinks(){
var jsnhttp = new XMLHttpRequest();
/*perform this function one page is loaded*/
jsnhttp.onreadystatechange = function() {
  if (this.status == 200 && this.readyState == 4) {
		/*declare variables and parse JSON file*/
   var i, n, z, tgsarr=[], tgsurlarr=[], jsnObj = JSON.parse(this.responseText);
		/*loop through each site (i)*/
		for(i in jsnObj){
			/*loop through each tag (n) in site (i)*/
			for(n in jsnObj[i].tags){
			/******check to see if tag already exists in array******/
				/*this function searches for the current category in tgsarr*/
				function fndvar(tgsarrval){return tgsarrval == jsnObj[i].tags[n]};
				
				/*if the current category is not found in the tgsarr variable (less than 0) then add it to the array*/
				/*if the current category is found in the tgsarr variable (>=0) then add the url to the existing category*/
				/*note: the tgsarr is a 1 dimension array used for searching to see if the category already is in the array*/
				if(tgsarr.findIndex(fndvar)<0){
					var z = tgsarr.push(jsnObj[i].tags[n]);
					/*create 2 dimension array of tag and url*/
					tgsurlarr.push(["<strong>" + tgsarr[z-1] + "</strong><br>", "<a id=" + jsnObj[i].title + " target=_blank href=" + jsnObj[i].url + ">" + jsnObj[i].title + "</a><br>"])
				}else{
					var z = tgsarr.findIndex(fndvar);
					tgsurlarr[z].push("<a id=" + jsnObj[i].title + " target=_blank href=" + jsnObj[i].url + ">" + jsnObj[i].title + "</a><br>")
				};
			}
		}
		/*Sort tagsurl array*/
		tgsurlarr.sort();
    
    /*Loop through each category array and sort each item*/
    for(n in tgsarr){
      	/*use shift to remove category from array*/
        /*using shift because Category is first element of the array*/
        var z = tgsurlarr[n].shift();
        /*sort links in array*/
        tgsurlarr[n].sort()
        /*Add Category back to array*/
        tgsurlarr[n].unshift(z);
      }
    
		/*lnks variable is set to the HTML paragraph*/
	  	/*use join, toString, and replace methods to remove commas from array
		If there is a comma in the title or url that will be replaced as well.
		this method also works but the "flat" method doesn't work on all browsers tgsurlarr.flat().join("")
		*/
		
		//document.getElementById("links").innerHTML = tgsurlarr.join("").toString().replace(/,/g,"");
		document.getElementById("links").innerHTML = tgsurlarr.join("").toString().replace(/,/g,"");
	}	
};
/*call site to get JSON data*/
jsnhttp.open("GET", jsonsite,true);
jsnhttp.send();
}
/*****END OF LINKS BY CATEGORY*****/
</script>
</html>
