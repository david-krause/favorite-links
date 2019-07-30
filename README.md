<html>
<p>
  Add links to <a href="links.json">JSON file</a>. <br>
  Only one Title and URL allowed.  One or more categories required. <br>
  Change "jsonsite" var in other html files to point to your json file.
</p>

<a href="links-all.html">All Links</a>
<br>
<a href="links-cat.html">Links by category</a>

<br><br>
<p id="links"></p>

<script>
/*Site that stores JSON file*/
var jsonsite="https://david-krause.github.io/favorite-links/links.json";
var jsnhttp = new XMLHttpRequest();
/*perform this function one page is loaded*/
jsnhttp.onreadystatechange = function() {
  if (this.status == 200 && this.readyState == 4) {
    var i, n, lnks=[], jsnObj = JSON.parse(this.responseText);
    for(i in jsnObj){
    	lnks.push("<a target='_blank' href=" + jsnObj[i].url + ">" + jsnObj[i].title + "</a><br>")
      }
    }
	lnks.sort();
     /*lnks variable is set to the HTML paragraph*/
	/*join method to remove commas*/
    document.getElementById("links").innerHTML = lnks.join("");
	};
/*call site to get JSON data*/
jsnhttp.open("GET", jsonsite,true);
jsnhttp.send();
</script>


</html>
