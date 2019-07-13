<html>
<body>

<p>
  Add links to JSON file using URL and Tags fields.
  This html file will parse and alphbetize the JSON file.
</p>

<p id="links"></p>

<script>
var JSN = '{"URL":"https://github.com}';
var Obj = JSON.parse(JSN);
document.getElementById("links").innerHTML = Obj.URL;
</script>

</body>
</html>
