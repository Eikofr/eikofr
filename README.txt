function loadJSON(callback) {
  var xhr = new XMLHttpRequest();
  xhr.overrideMimeType("application/json");
  xhr.open("GET", "test.json", true);
  xhr.onreadystatechange = function() {
    if (xhr.readyState === 4 && xhr.status === 200) {
      cle = JSON.parse(xhr.responseText)["1"]; // stocke la valeur de la clé dans la variable globale
      if (callback) {
        callback(cle);
      }
    }
  };
  xhr.send(null);
}
