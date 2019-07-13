<html>
<body>
<p>
  Add links to JSON file using URL and Tags fields.<br>
  This html file will parse and alphbetize the JSON file.
</p>

<p id="links"></p>

<script>
var JSN = {site.url}.{site.title}/links.json;
var Obj = JSON.parse(JSN);
  
for (i in Obj) {
  x += myObj[i].title;
}
document.getElementById("links").innerHTML = x;



</script>

</body>
</html>
