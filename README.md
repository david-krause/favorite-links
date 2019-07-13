<html>
<body>
<p>
  Add links to JSON file using URL and Tags fields.<br>
  This html file will parse and alphbetize the JSON file.
</p>

<p id="links"></p>
<script>


var JSN = json;
var Obj = JSON.parse(JSN);
document.getElementById("links").innerHTML = Obj.URL + " " + Obj.title;
</script>

</body>
</html>
