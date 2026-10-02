<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Project ITECH API Test</title>
</head>

<body>

<h1>Project ITECH API Test</h1>

<div id="status">
  Connecting to Google Apps Script...
</div>

<div id="result"></div>

<script>

  function testProducts(data) {

    console.log("API DATA:", data);

    document.getElementById("status").innerHTML =
      "✅ SUCCESS: Google Apps Script is connected!";

    if (!data || data.length === 0) {

      document.getElementById("result").innerHTML =
        "<p>No approved products found.</p>";

      return;
    }

    const product = data[0];

    document.getElementById("result").innerHTML = `
      <hr>

      <h2>${product.productName}</h2>

      <p>
        ${product.productDescription}
      </p>

      <p>
        Student: ${product.studentName}
      </p>

      <img
        src="${product.imageUrl}"
        style="max-width:500px; width:100%;"
      >
    `;

  }


  const script = document.createElement("script");

  script.src =
    "https://script.google.com/macros/s/AKfycbyO7BaYkjDmcg2asavZbvPFYpSFr_Uz7ntEUMyWEw-25QF-pzeDBl573Vx1VFw4snXyvw/exec" +
    "?api=products&callback=testProducts";

  script.onerror = function() {

    document.getElementById("status").innerHTML =
      "❌ ERROR: GitHub could not connect to Google Apps Script.";

  };


  document.body.appendChild(script);

</script>

</body>
</html>
